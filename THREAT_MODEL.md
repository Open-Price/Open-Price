# Open-Price Threat Model

This document identifies high-level threats to users, data, and the Open-Price project,
and documents early design principles for mitigating harm.

This threat model is intentionally practical and human-readable.
It will evolve as the system evolves.

---

## Scope & Assumptions

Open-Price is a consumer-facing, privacy-first, open-source application that enables
crowd-sourced reporting of product prices across stores and locations.

### In Scope
- User-submitted price data
- Optional photos and barcode scans
- Store-level information (name, address, phone)
- Coarse, opt-in location data
- Public, non-personal pricing information

### Out of Scope
- User accounts by default
- Advertising or tracking systems
- Personalized pricing
- Behavioral profiling
- Real-time surveillance of users

Threats are evaluated within these boundaries.

---

## Core Assets

The following assets are considered critical and must be protected by design:

1. **User privacy**
2. **Integrity of price data**
3. **Transparency and credibility of the project**
4. **Trust of contributors and users**
5. **Availability and resilience of the system**

Any feature or architectural decision must be evaluated against its impact on these assets.

---

## Threat Categories

### 1. Privacy Risks

**Potential Threats**
- Location data becoming more precise than intended
- Accidental exposure of personal information in photos
- Leakage of metadata (timestamps, EXIF data)
- Introduction of tracking libraries by future contributors

**Design-Level Mitigations**
- Coarse location by default; precise location always opt-in
- Clear permission prompts for camera and location access
- Automatic stripping of metadata from uploaded images
- Dependency review and prohibition of tracking SDKs
- Privacy regression review for new features

---

### 2. Data Integrity & Manipulation Risks

**Potential Threats**
- Submission of false or misleading prices
- Coordinated manipulation by bad actors or interested parties
- Stale prices presented as current
- Reuse or fabrication of verification photos

**Design-Level Mitigations**
- Timestamping of price submissions
- Clear labeling of data age and freshness
- Community validation mechanisms (confirm / flag)
- Rate limiting for anonymous submissions
- Reputation signals based on accuracy, not identity

---

### 3. Abuse & Harassment Risks

**Potential Threats**
- Targeting or harassment of specific stores or workers
- Spam or malicious submissions
- Data poisoning for competitive or political purposes

**Design-Level Mitigations**
- Focus on store-level data only; no individual employee data
- Clear acceptable-use guidelines
- Community moderation tools
- Ability to flag abusive or suspicious content
- Transparent moderation practices

---

### 4. Legal & Regulatory Risks

**Potential Threats**
- Claims that pricing data was scraped rather than user-submitted
- Misuse of takedown or legal threats to suppress transparency
- Jurisdictional data-handling concerns
- Misinterpretation as enabling price fixing

**Design-Level Mitigations**
- Clear framing of all pricing data as user-submitted
- Public documentation of methodology and data sources
- Avoidance of features that enable coordinated pricing behavior
- Conservative, transparent legal posture
- Open-source transparency to support good-faith use

---

### 5. Infrastructure & Availability Risks

**Potential Threats**
- Denial-of-service attacks
- Infrastructure cost overruns
- Centralized points of failure
- Loss of service during peak usage

**Design-Level Mitigations**
- Local-first architecture where possible
- Offline capture with delayed synchronization
- Graceful degradation of non-essential features
- Conservative infrastructure assumptions
- Avoidance of unnecessary centralization

---

## Guiding Principle

If a proposed mitigation requires surveillance, tracking, coercion,
or erosion of user privacy, it is not an acceptable solution.

Open-Price prioritizes harm reduction through transparency,
user agency, and minimal data collection.
