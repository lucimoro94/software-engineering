# Requirements Specification

**Version**: 1.1  
**Last Updated**: 
**Author**: Development Team

## Functional Requirements

### FR1: Product Catalog Management

- Display 80+ products with real-time availability
- Filter by: category, seasonality, price, package size
- Multi-language support (IT, EN, DE, FR)
- Batch tracking with QR codes for each product
- Nutritional info and allergen warnings
- High-resolution images (min 3 per product)
- PDF generation for product specifications

### FR2: User Management (B2B Focus)

- Company registration with VAT validation
- Multiple users per company account
- Role-based access (Buyer, Manager, Accountant)
- Credit line management (€5,000 - €50,000)
- Automatic credit check via Creditsafe API
- Two-factor authentication mandatory

### FR3: Order Processing

- Minimum order value: €500
- Bulk discount tiers:
  - €500-1000: list price
  - €1000-5000: -5%
  - €5000+: -10%
- Recurring order templates
- Order modification up to 24h before delivery
- Split delivery options

### FR4: Payment & Invoicing

- SEPA Direct Debit (primary)
- Bank transfer with 30/60/90 days terms
- Electronic invoicing (compliant with Italian/EU standards)
- **NO credit card processing** (after security review)
- Automated dunning for overdue payments

### FR5: Inventory & Freshness

- Real-time stock levels
- Automatic FIFO rotation
- Expiry alerts (7, 3, 1 day before)
- Seasonal availability calendar
- Pre-order for seasonal items
- Waste tracking and reporting

### FR6: Integration Capabilities

- RESTful API for order placement
- Webhook notifications for order status
- CSV/Excel export for all data
- ERP integration (SAP, Oracle, Microsoft)
- **Simplified after discussion**: No EDI in v1

## Non-Functional Requirements

### NFR1: Performance

- Page load time: <2 seconds (European users)
- API response time: <500ms for 95% of requests
- Support 500 concurrent users
- 99.9% uptime SLA
- CDN for static assets

### NFR2: Security

**Critical - Added after stakeholder discussion**

- OWASP Top 10 compliance
- Input validation against SQL injection
- XSS protection on all forms
- CSRF tokens for state-changing operations
- PCI DSS not required (no credit cards)
- GDPR compliant
- Penetration testing before launch
- WAF (Web Application Firewall) mandatory
- Rate limiting on API endpoints
- Encrypted data at rest and in transit

### NFR3: Scalability

- Cloud-native architecture (AWS Milan region)
- Auto-scaling for peak seasons
- Database read replicas
- Microservices architecture for future growth
- Container-based deployment (Docker/Kubernetes)

### NFR4: Usability

- Mobile-responsive design
- Works on tablets (warehouse staff use iPads)
- Accessibility WCAG 2.1 Level AA
- Available in 4 languages

## Technical Constraints

### Technology Stack (After Discussion)

- **Frontend**: Next.js 14 with TypeScript
- **Backend**: Node.js with Express
- **Database**: PostgreSQL (main) + Redis (cache)
- **Cloud**: AWS (EU-CENTRAL-1 and EU-SOUTH-1)
- **Container**: Docker with Kubernetes
- **CI/CD**: GitHub Actions
- **Monitoring**: Datadog
- **CDN**: CloudFront

### Development Constraints

- Budget: €40,000 
- Team: 2 senior devs, 1 junior, 1 DevOps
- Timeline: 6 months to production
- Code coverage: Minimum 80%
- Documentation: OpenAPI 3.0 for all endpoints

## Out of Scope (Version 1.0)

### Explicitly Excluded After Discussions:

1. **Blockchain tracking** - Too expensive, low ROI
2. **AI demand forecasting** - Need historical data first
3. **Mobile native apps** - PWA sufficient for now
4. **Multi-warehouse system** - Single hub + partners
5. **EDI integration** - Only 2 clients need it
6. **Subscription boxes** - Different business model
7. **Direct farm integration** - Manual process for now
8. **Customer portal customization** - Standard UI for all

### Planned for Version 2.0:

- Machine learning for demand prediction (after 12 months)
- Advanced analytics dashboard
- Multi-warehouse inventory sync
- Automated quality control with computer vision
- Dynamic pricing based on demand/seasonality

## Risk Analysis

### Technical Risks:

1. **ERP Integration complexity**: Mitigated by phased rollout
2. **GDPR compliance**: Legal review required
3. **Scalability during peak season**: Load testing planned
4. **Security breaches**: Pen testing + WAF + insurance

### Business Risks:

1. **Competitor response**: Fast time-to-market critical
2. **Client adoption**: Training program planned
3. **Seasonality impact**: Focus on preserved products for winter

## Acceptance Criteria

- Pass security audit by external firm
- Load testing: 1000 concurrent users
- 100% of critical user journeys tested
- Documentation complete
- GDPR compliance verified
- 5 pilot customers successful