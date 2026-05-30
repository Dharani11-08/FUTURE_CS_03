# FUTURE_CS_03
# API Security Risk Analysis Report

## Overview

This project focuses on conducting an API Security Risk Analysis using the public JSONPlaceholder REST API as part of the Future Interns CyberSecurity Internship Program.

The assessment was performed in a safe and ethical manner using read-only testing techniques to identify common API security risks such as unauthenticated access, excessive data exposure, authorization weaknesses, and input validation behavior.

The project demonstrates practical API security analysis skills using tools like Postman, Browser Developer Tools, and public API documentation.

---

## Introduction

Modern applications rely heavily on APIs (Application Programming Interfaces) for communication between:

- Mobile applications
- Web applications
- SaaS platforms
- Backend services

APIs often handle sensitive information and business-critical operations. Improper API security can lead to:

- Unauthorized access
- Data leakage
- Broken authorization
- Abuse of backend services

This project focuses on identifying API security risks through ethical and read-only testing.

---

## Objectives

The main objectives of this project are:

- Analyze public/demo APIs safely
- Identify common API security risks
- Review authentication and authorization mechanisms
- Inspect API responses and HTTP headers
- Assess overall API security posture
- Suggest remediation recommendations
- Document findings professionally

---

## Scope of Analysis

### Allowed Activities

- Read-only API testing
- Documentation-based analysis
- Header inspection
- Response analysis
- Endpoint testing

### Restricted Activities

The following activities were strictly avoided:

- Exploitation attempts
- Authentication bypass testing
- Brute-force attacks
- Denial-of-Service (DoS) testing
- Private API testing

The assessment was conducted only on a public demo API intended for learning and educational purposes.

---

## API Selected for Analysis

| API Name | JSONPlaceholder |
|----------|----------------|
| Base URL | https://jsonplaceholder.typicode.com |
| Purpose | Public fake REST API for testing and prototyping |

### Sample Resources Available

- Users
- Posts
- Photos
- Comments
- Albums

---

## Tools Used

| Tool | Purpose |
|------|----------|
| Postman | API request testing and response analysis |
| Browser Developer Tools | Header and request inspection |
| Google Chrome | Endpoint testing |
| JSONPlaceholder API | Public API testing environment |
| GitHub | Project documentation and submission |

---

## Testing Methodology

The following methodology was followed during the analysis:

### Step 1: API Endpoint Testing

The following endpoints were tested:

```http
/users
/photos
/users/3
/users?id=2
```

### Step 2: Authentication Review

The Authorization section in Postman was inspected to determine whether:

- API tokens were required
- Authentication credentials existed
- Access control mechanisms were implemented

### Step 3: Header Analysis

HTTP response headers were inspected to analyze:

- Security headers
- Rate limiting
- Server information
- Response behavior

### Step 4: Input Validation Testing

Invalid endpoint testing was performed using random input to observe:

- Error handling
- Response behavior
- System stability

### Step 5: Documentation of Findings

All observations were documented with supporting screenshots and analysis.

---

# Findings and Risk Analysis

---

## Finding 1: Open API Endpoint Access

### Observation

The `/users` endpoint was accessible without authentication, API tokens, or login credentials.

### Example Endpoint

```http
GET /users
```

### Risk Type

Open / Unauthenticated Endpoint

### Severity

Medium

### Business Impact

In real-world systems, unauthenticated access may expose sensitive user information to unauthorized users, leading to:

- Privacy risks
- Information leakage
- Data exposure

### Recommendation

Implement secure authentication mechanisms such as:

- API Tokens
- OAuth 2.0
- JWT Authentication

Sensitive endpoints should require proper authentication and authorization.

---

## Finding 2: Excessive Data Exposure

### Observation

The API response exposed excessive user information including:

- Email addresses
- Phone numbers
- Address details
- Geo-location data
- Company information

### Risk Type

Excessive Data Exposure

### Severity

Medium

### Business Impact

Exposing unnecessary user information may:

- Increase privacy risks
- Help attackers gather intelligence
- Leak internal business details

### Recommendation

Return only the minimum required fields based on business necessity.

### Example

Instead of returning complete user profiles, expose only essential data.

---

## Finding 3: Authorization Weakness (Potential IDOR Risk)

### Observation

User-specific data was directly accessible through:

```http
/users/3
```

Changing the ID could expose other user records:

```http
/users/1
/users/2
```

### Risk Type

Broken Object Level Authorization (Potential IDOR)

### Severity

Medium

### Business Impact

Attackers may manipulate object IDs to access unauthorized user data, potentially causing:

- Unauthorized information disclosure
- Privacy violations
- Account data exposure

### Recommendation

Implement server-side authorization checks to validate user ownership before returning sensitive information.

---

## Finding 4: Rate Limiting Present (Positive Security Practice)

### Observation

The response headers contained:

```http
x-ratelimit-limit = 1000
```

### Security Observation

Positive Security Control

### Business Impact

Rate limiting helps prevent:

- API abuse
- Excessive requests
- Brute-force attacks
- Server overload

### Recommendation

Continue enforcing:

- Request throttling
- Traffic monitoring
- Abuse detection mechanisms

---

## Finding 5: Input Validation Observation

### Observation

An invalid endpoint was tested:

```http
/dfgh
```

The API returned an empty response instead of exposing server errors or crashing.

### Risk Type

Input Validation Observation

### Severity

Low

### Business Impact

Proper handling of invalid input improves:

- System stability
- Secure error handling
- Application reliability

### Recommendation

Continue implementing standardized HTTP error handling and secure validation mechanisms.

---

## Risk Summary Table

| Risk | Severity | Business Impact | Recommendation |
|------|----------|----------------|---------------|
| Open Endpoint Access | Medium | Unauthorized Access | Add Authentication |
| Excessive Data Exposure | Medium | Information Leakage | Restrict Unnecessary Fields |
| Authorization Weakness | Medium | Unauthorized User Access | Validate Permissions |
| Rate Limiting Present | Positive | Protection Against Abuse | Continue Enforcement |
| Input Validation Observation | Low | Better Stability | Maintain Validation |

---

## Key Learning Outcomes

This project helped develop practical knowledge in:

- API inspection
- Security analysis
- Authentication assessment
- Risk identification
- Security documentation
- SaaS security fundamentals

---

## Project Structure

```bash
├── README.md
├── FutureInternsTask3.pdf
├── screenshots/
│   ├── image1.png
│   ├── image2.png
│   ├── image3.png
│   ├── image4.png
│   └── image5.png
```

---

## How to Use

### Clone the Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
```

### Open the Project Folder

```bash
cd your-repository-name
```

### Review the Report

Open the PDF report and screenshots to view the complete API security analysis.

---

## Conclusion

This project successfully conducted a read-only API Security Risk Analysis using the JSONPlaceholder public API.

The assessment identified important API security considerations including:

- Open endpoint accessibility
- Excessive data exposure
- Authorization weaknesses
- Rate limiting implementation
- Input validation behavior

Although JSONPlaceholder is intentionally public for educational purposes, the findings reflect real-world API security risks that organizations must address in production environments.

---

## Disclaimer

This project was created strictly for educational and ethical cybersecurity learning purposes.

All testing was performed only on publicly available demo APIs designed for safe educational use.

No exploitation or harmful activity was performed.

---
