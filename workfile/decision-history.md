# Decision History

**Project**: FreshCut B2B E-commerce Platform  
**Period**:   
**Participants**:student1, student 2 (Stakeholder), Dev Team Lead student 2, 3

---

## Decision 1: Blockchain for Supply Chain Tracking

### Stakeholder Proposal (Saturday, 10:30 AM)

"We absolutely need blockchain! Every product should be tracked from farm to delivery. Imagine - customers scan a QR code and see the exact tree their apples came from! IBM and Walmart are doing it, we should too. This will be our competitive advantage!"

### Developer Analysis (Saturday, 2:00 PM)

"I researched this thoroughly:

- IBM Food Trust shut down in 2023 after burning through $100M
- Walmart's blockchain tracks only 1% of products after 5 years of trying
- Cost: ~€100k/year just for infrastructure
- Our farmers don't have the tech capability to input data
- Customers care about freshness, not which tree it came from
- Regular batch tracking achieves 95% of the benefits"

### Discussion Thread (Saturday, 2:30 - 4:00 PM)

**Stakeholder**: "But everyone talks about blockchain! Our investors will love it!"

**Developer**: "Let me show you real numbers:

- Carrefour implemented blockchain in 2019, removed it in 2023
- Cost per transaction: €0.50 with blockchain vs €0.001 with traditional database
- Query speed: 2-3 seconds blockchain vs 50ms traditional
- Customer surveys show only 3% care about blockchain specifically"

**Stakeholder**: "What if our competitors launch with blockchain?"

**Developer**: "They won't. I checked - they're all moving away from it. What customers want is simple: fresh products, on time, with clear expiry dates. QR codes with batch tracking give them this."

### Final Decision (Saturday, 4:30 PM)

**No blockchain in V1**. Use QR codes with traditional database for batch tracking. 

### Rationale

- Save €100k+ in year one
- 1000x faster queries
- Same transparency for customers
- Can always add blockchain later if market demands it (unlikely)
- Focus budget on features that directly impact customer experience

---

## Decision 2: Geographic Coverage & Warehouse Strategy

### Stakeholder Proposal (Saturday, 11:00 AM)

"We need three warehouses from day one: Milan, Rome, and Berlin. This gives us coverage across Italy and Germany. We can't compete without same-day delivery in major cities!"

### Developer Analysis (Saturday, 4:00 PM)

"Multi-warehouse means:

- 3x inventory management complexity
- Real-time sync issues (split-brain scenarios)
- 3x staff training costs
- Different regulations per region
- Initial setup: €200k per warehouse
- Tech complexity increases exponentially, not linearly"

### Discussion Thread (Saturday, 5:00-6:30 PM)

**Stakeholder**: "But customers expect fast delivery!"

**Developer**: "Let's look at alternatives:

- Partner with local cold-chain couriers
- They already have infrastructure
- We maintain central quality control
- Cost: €30k setup vs €600k for 3 warehouses"

**Stakeholder**: "What about inventory availability?"

**Developer**: "One central warehouse with smart routing:

- Milan reaches 80% of Northern Italy in 24h
- Partner hubs for same-day in Rome/Berlin
- We control quality from one location
- Easier to maintain freshness standards"

**Stakeholder**: "Show me the numbers..."

**Developer**: "Simulation results:

- 1 warehouse + partners: 24h for 85% of orders
- 3 warehouses: 24h for 92% of orders
- Cost difference: €570k in year one
- Is 7% improvement worth €570k?"

### Final Decision (Saturday, 6:30 PM)

**Single Milan warehouse + courier partnerships**

### Rationale

- €570k cost saving in year one
- Maintains 24-48h delivery promise
- Simplifies inventory management
- Single source of truth for stock
- Can expand to multi-warehouse in year 2 if needed
- Focus on software excellence vs hardware distribution

---

## Decision 3: Payment Security & Methods

### Initial Situation (Sunday, 10:00 AM)

**Stakeholder**: "We need to accept all payment methods - credit cards, PayPal, cryptocurrency, everything!"

### Developer Security Concern (Sunday, 10:30 AM)

"Credit card processing in B2B is a major security risk:

- PCI DSS compliance costs €15k/year minimum
- We become target for hackers
- Recent breach at competitor cost them €500k
- B2B clients prefer invoices anyway (tax benefits)
- Card processing fees: 2.9% + €0.30 per transaction"

### Discussion Thread (Sunday, 11:00 AM - 12:00 PM)

**Stakeholder**: "But it's convenient for customers!"

**Developer**: "Our research shows:

- 89% of B2B transactions are bank transfer or direct debit
- Credit cards are 8% and declining
- Card fraud in B2B food sector increased 400% last year
- SEPA Direct Debit costs €0.35 flat fee vs 2.9% for cards"

**Stakeholder**: "What about new customers who want to try us?"

**Developer**: "Solutions:

1. First order via bank transfer (builds trust)
2. After verification, enable SEPA Direct Debit
3. For trusted clients: 30/60/90 day payment terms
4. This is industry standard for B2B"

**Stakeholder**: "The security risks are really that bad?"

**Developer**: "Last month's breach at FoodSupplier.it:

- 10,000 credit cards stolen
- €2M in fraudulent charges
- Business shut down for 2 weeks
- Lost 30% of customers permanently
- They had PCI compliance but still got hacked"

### Final Decision (Sunday, 12:15 PM)

**No credit card processing. SEPA Direct Debit + Bank Transfer only**

### Rationale

- Eliminate major security attack vector
- Save €15k/year PCI compliance
- Save 2.9% on every transaction
- Match industry B2B standards
- Reduce fraud risk by 95%
- Can add cards later if absolutely necessary

---

## Decision 4: Technology Stack

### Stakeholder Proposal (Sunday, 9:00 AM)

"I've heard great things about Web3, serverless, and microservices. We should use the latest tech! Also, my friend says Ruby on Rails is amazing."

### Developer Analysis (Sunday, 1:00 PM)

"Let's evaluate based on our needs:

- Team knows JavaScript/TypeScript best
- Next.js gives us SSR for SEO
- Node.js has mature B2B libraries
- PostgreSQL handles complex B2B queries
- AWS Milan region for GDPR compliance"

### Discussion Thread (Sunday, 1:30-2:30 PM)

**Stakeholder**: "But microservices are the future!"

**Developer**: "Microservices for our size means:

- 10x operational complexity
- Need dedicated DevOps team (€100k/year)
- Network latency between services
- Distributed transaction headaches
- Netflix uses microservices. Netflix has 2,500 engineers. We have 4."

**Stakeholder**: "What about serverless? No servers to manage!"

**Developer**: "Serverless has hidden costs:

- Cold starts: 2-5 second delays
- Vendor lock-in to AWS
- Debugging is nightmare
- Costs unpredictable at scale
- Our B2B load is predictable - perfect for traditional servers"

**Stakeholder**: "Fine, but why not Java or .NET? More enterprise!"

**Developer**: "Team productivity comparison:

- JavaScript/TypeScript: Team ships features in 2 days
- Java: Same features take 5 days (we'd need to learn)
- Hiring: 1000 Node.js devs in Milan vs 200 Java devs
- Libraries: NPM has every B2B integration we need"

### Final Decision (Sunday, 2:45 PM)

**Modern but proven stack: Next.js + Node.js + PostgreSQL + AWS**

### Rationale

- Team expertise = faster delivery
- Proven at scale (used by Walmart.com)
- Great ecosystem for B2B integrations
- Strong security libraries available
- Can hire easily when scaling
- Not bleeding edge = fewer surprises

---

## Decision 5: Budget Allocation

### Initial Stakeholder Position (Saturday, 9:00 AM)

"€35,000 should be enough. My cousin made an e-commerce for €10,000!"

### Developer Breakdown (Saturday, 5:00 PM)

"B2B platform real costs:

- Development (4 devs × 3 months): €24,000
- Security audit: €5,000
- Infrastructure setup: €3,000
- ERP integration licenses: €4,000
- Testing & QA: €3,000
- Documentation: €2,000
- Buffer for unknowns: €4,000
  Total: €45,000 minimum"

### Negotiation (Sunday, 3:00 PM)

**Stakeholder**: "Can we cut something?"

**Developer**: "What we could cut and consequences:

- Skip security audit: Risk €500k breach
- Skip documentation: Future devs cost 3x more
- Skip testing: Launch with bugs, lose customers
- Skip ERP integration: Lose enterprise clients"

**Stakeholder**: "I understand. What if we phase it?"

**Developer**: "Smart approach:

- Phase 1 (€40k): Core platform + security + basic integration
- Phase 2 (€20k): Advanced features + optimizations
- This reduces initial investment while maintaining security"

### Final Decision (Sunday, 4:00 PM)

**€40,000 for Phase 1, option for €20,000 Phase 2**

### Rationale

- Security and core features non-negotiable
- Phased approach reduces risk
- Can generate revenue before Phase 2
- Stakeholder comfortable with investment
- Quality over speed prevents technical debt

---

## Meta Decision: Decision-Making Process

### Evolution Over Weekend

**Saturday Morning**: Stakeholder had grand visions, developer was skeptical
**Saturday Afternoon**: Data and examples started changing minds  
**Sunday Morning**: Stakeholder began asking "why" instead of demanding
**Sunday Afternoon**: True collaboration emerged

### Key Learning

- Real data beats assumptions
- Security cannot be compromised for features
- Simple and working beats complex and maybe
- Industry standards exist for good reasons
- Technical debt is more expensive than doing it right

### Final Stakeholder Comment (Sunday, 5:00 PM)

"I came in thinking technology was magic. Now I understand it's about trade-offs. Every feature has a cost - not just money, but complexity, security risk, and maintenance. Let's build something solid, not something flashy."

### Developer Response

"This is why I love working with smart stakeholders. You pushed me to explain better, and I pushed back with data. The platform we're building is better because of our discussions, not despite them."