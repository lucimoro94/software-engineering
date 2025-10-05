# Use Cases Documentation

**System**: FreshCut B2B E-commerce Platform  
**Version**: 1.0  
**Date**: 

## Actors

### Primary Actors:

1. **Guest User**: Potential B2B client browsing catalog
2. **Registered Buyer**: Authorized to make purchases for their company
3. **Company Manager**: Manages users and credit for their company
4. **Admin**: FreshCut staff managing platform
5. **Warehouse Staff**: Handles inventory and orders

### Secondary Actors:

- **ERP System**: External integration
- **Payment Gateway**: SEPA processing
- **Delivery Service**: Courier API

## Use Case List

### UC1: Browse Product Catalog

**Actor**: Guest User, Registered Buyer  
**Precondition**: User has internet access  
**Main Flow**:

1. User accesses website
2. System displays product categories
3. User filters by type (fruits/vegetables/preparations)
4. User filters by seasonality
5. System shows available products with prices
6. User views product details
7. User downloads product specification PDF

**Alternative Flow**:

- 3a. Product out of season → System shows "Available in [month]"
- 5a. User not logged in → Sees "Login for prices"

### UC2: Company Registration

**Actor**: Company Manager  
**Precondition**: Valid VAT number  
**Main Flow**:

1. User clicks "Register Company"
2. User enters company details and VAT
3. System validates VAT via VIES API
4. User uploads business documents
5. System creates account (pending approval)
6. Admin reviews and approves
7. System sends credentials via email

**Alternative Flow**:

- 3a. Invalid VAT → Show error, stop registration
- 6a. Admin rejects → Email with requirements

### UC3: Place Order with Credit

**Actor**: Registered Buyer  
**Precondition**: Active account with available credit  
**Main Flow**:

1. Buyer logs in with 2FA
2. Buyer adds products to cart (min €500)
3. System checks inventory availability
4. System calculates bulk discounts
5. Buyer selects delivery date
6. System verifies credit limit
7. Buyer confirms order
8. System reserves inventory
9. System sends order confirmation
10. System generates e-invoice

**Alternative Flow**:

- 3a. Insufficient stock → Suggest alternative date
- 6a. Credit exceeded → Request payment upfront
- 5a. Delivery slot full → Show next available

### UC4: Manage Recurring Orders

**Actor**: Registered Buyer  
**Precondition**: Previous successful orders  
**Main Flow**:

1. Buyer accesses "My Templates"
2. Buyer creates template from past order
3. Sets recurrence (weekly/biweekly/monthly)
4. Sets quantity adjustments per season
5. System schedules automatic orders
6. System sends reminder 48h before each order
7. Buyer can modify/skip upcoming order

**Exception Flow**:

- 6a. Product unavailable → Email alert, skip item

### UC5: Track Product Freshness

**Actor**: Warehouse Staff, Admin  
**Precondition**: Products in inventory  
**Main Flow**:

1. Staff scans product QR code on arrival
2. System records batch number and expiry
3. System assigns to FIFO queue
4. Daily: System checks all expiries
5. System alerts for products <3 days to expiry
6. Staff marks products for promotion/disposal
7. System updates availability

**Alternative Flow**:

- 6a. Product near expiry → Auto-discount 20%

### UC6: Integration with Client ERP

**Actor**: ERP System  
**Precondition**: API credentials configured  
**Main Flow**:

1. ERP sends authentication request
2. System validates OAuth token
3. ERP sends order via API
4. System validates order data
5. System checks business rules
6. System confirms order
7. System sends webhook on status change

**Error Handling**:

- 2a. Invalid token → 401 Unauthorized
- 4a. Malformed request → 400 Bad Request
- 5a. Credit limit exceeded → 402 Payment Required

### UC7: Generate Reports

**Actor**: Company Manager, Admin  
**Precondition**: Appropriate permissions  
**Main Flow**:

1. User selects report type
2. User sets date range
3. System queries database
4. System generates report
5. User downloads as CSV/PDF
6. System logs access for audit

**Report Types**:

- Order history
- Invoice summary  
- Product performance
- Waste analysis
- Delivery performance

### UC8: Handle Returns/Complaints

**Actor**: Registered Buyer, Admin  
**Precondition**: Delivered order  
**Main Flow**:

1. Buyer reports issue within 24 hours
2. Buyer uploads photo evidence
3. System creates ticket
4. Admin reviews complaint
5. Admin approves credit/replacement
6. System processes refund
7. System updates quality metrics

**Alternative Flow**:

- 4a. Complaint rejected → Provide reason
- 5a. Replacement → Schedule new delivery

### UC9: Manage Credit Limits

**Actor**: Admin, Company Manager  
**Precondition**: Active company account  
**Main Flow**:

1. Manager requests credit increase
2. System runs credit check via Creditsafe
3. Admin reviews financial data
4. Admin sets new credit limit
5. System notifies manager
6. System updates payment terms

**Risk Management**:

- 2a. Poor credit score → Require prepayment
- 3a. Overdue invoices → Freeze account

### UC10: Security Monitoring

**Actor**: System (Automated)  
**Trigger**: Every request  
**Main Flow**:

1. System validates input against XSS patterns
2. System checks SQL injection attempts
3. System verifies CSRF tokens
4. System applies rate limiting
5. System logs suspicious activity
6. If threat detected → Block and alert admin

**Security Measures**:

- Input sanitization
- Parameterized queries
- Session management
- API rate limiting (100 requests/minute)
- WAF rules active

## Use Case Diagram Description

The diagram shows:

- **Guest Users** can only browse catalog
- **Registered Buyers** can place orders and manage templates
- **Company Managers** oversee users and credit
- **Admin** has full system control
- **Warehouse Staff** manages inventory
- **External Systems** (ERP, Payment) integrate via API

Key relationships:

- Registration extends to credit check
- Orders include inventory check
- All financial operations include security validation
- Reports generation includes audit logging