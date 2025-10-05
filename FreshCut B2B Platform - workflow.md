# FreshCut B2B Platform - Student Team Guide

## PROJECT STATUS: 80% COMPLETE - NEEDS YOUR REVIEW & GITHUB WORKFLOW

**Important**: The files in `docs/` folder are 80% complete drafts. You must review, modify, and improve them according to your role before uploading to GitHub. This guide explains the complete workflow.

---

## REPOSITORY SETUP (One person does this FIRST)

**Who**: Either Matteo, Luciano, or Pedro (decide among yourselves)

```bash
# 1. Create private repository on GitHub
Repository name: freshcut-b2b-platform
Visibility: PRIVATE
Initialize with README: YES

# 2. Add collaborators
Settings → Collaborators → Add people
Add the other two team members by their GitHub usernames

# 3. Clone and create folder structure
git clone https://github.com/[your-username]/freshcut-b2b-platform.git
cd freshcut-b2b-platform
mkdir -p docs/requirements docs/diagrams
git add .
git commit -m "chore: initial project structure"
git push origin main
```

---

## MATTEO'S TASKS (Business Owner / Stakeholder)

### YOUR FILES TO REVIEW:

1. `stakeholder-interviews.md` 
2. `decision-history.md`

### STEP 1: Review & Modify Stakeholder Interviews (TODAY 8:00 PM)

**What to change:**

- Add today's actual date where you see empty date fields
- Review business requirements - add or remove anything you want
- **Important**: Keep the "ambitious requests" (blockchain, 3 warehouses) initially - this creates the discussion
- You can modify budget numbers, product types, market focus as you prefer
- Make sure the business vision reflects realistic B2B e-commerce needs

**Your character**: You're the business owner who wants the best technology but is willing to learn from technical feedback.

```bash
# Create your branch
git checkout -b feature/business-requirements

# After reviewing and modifying the file:
git add docs/requirements/stakeholder-interviews.md
git commit -m "feat: add stakeholder interviews with business vision"
git push origin feature/business-requirements
```

**Create Pull Request #1:**

- Go to GitHub repository

- Click "Pull Requests" → "New Pull Request"

- Base: main ← Compare: feature/business-requirements

- Title: `Business requirements and stakeholder vision`

- Description: 
  
  ```
  Initial business requirements from stakeholder perspective.
  ```

Key requests:

- Blockchain for supply chain tracking
- 3 warehouses (Milan, Rome, Berlin)
- AI-powered demand forecasting
- Budget: €35,000

Looking forward to technical team feedback on feasibility.

```
### STEP 2: Wait for Team Comments (9:00 PM - 10:00 PM)

Luciano and Pedro will comment on your PR. Read their technical concerns carefully.

### STEP 3: Respond to Feedback (10:00 PM)

**In PR #1 comments, write something like:**
```

After reviewing the data provided by @luciano about blockchain failures 
(IBM Food Trust, Walmart's limited success), I understand the cost vs benefit 
doesn't justify it for our scale. 

Let's go with QR codes + batch tracking instead. Can you update the technical 
specs accordingly?

```
**Then update the file:**
```bash
# Modify stakeholder-interviews.md - remove/adjust blockchain references
git add docs/requirements/stakeholder-interviews.md
git commit -m "fix: remove blockchain requirement after team feedback"
git push origin feature/business-requirements
```

### STEP 4: Review Technical Specs (TOMORROW 10:00 AM)

When Luciano creates PR #2, you must comment with additional business needs:

```
Technical specs look solid. Two additions needed:

1. Italian e-invoicing (FatturaPA) - mandatory for our market
2. SAP integration for enterprise clients (they requested this)

Can we include these in v1 or should they go to v2?
```

### STEP 5: Create Decision History (TOMORROW 3:00 PM)

This is your final contribution showing the team's learning process.

**Review and complete `decision-history.md`:**

- Add all actual dates from your discussions
- Add real quotes from GitHub PR comments
- Show evolution: ambitious → realistic
- Include final compromises reached

```bash
git checkout -b feature/decision-history

# After completing the file with real dates and quotes:
git add docs/requirements/decision-history.md
git commit -m "docs: add complete decision history

Co-authored-by: Luciano <luciano@email.com>
Co-authored-by: Pedro <pedro@email.com>"
git push origin feature/decision-history
```

**Create Pull Request #4:**

- Title: `Decision history - our learning journey`

- Description:
  
  ```
  Complete decision history documenting our team's learning process.
  ```

Shows how we evolved from ambitious initial requirements to pragmatic, 
secure, and cost-effective solutions.

Key learnings:

- Blockchain → QR codes (saved €100k/year)

- 3 warehouses → 1 hub + partners (saved €570k)

- Credit cards → SEPA only (eliminated security risk)

- Complex tech → proven stack (faster delivery)
  
  ```
  
  ```

---

## LUCIANO'S TASKS (Senior Developer / Tech Lead)

### YOUR FILE TO REVIEW:

1. `requirements-specification.md`

### STEP 1: Review & Modify Requirements (TODAY 10:30 PM)

**What to change:**

- Add today's actual date and version number
- **Critical**: Review all security requirements - add or modify based on OWASP guidelines you know
- Adjust technology stack if you prefer different tools (but keep it realistic for the team)
- Review NFRs (performance, scalability) - modify numbers based on realistic expectations
- You can completely change the "Out of Scope" section
- Adjust budget if needed (current draft shows €40k)

**Your character**: Experienced developer focused on security, pragmatic solutions, and educating the junior developer.

```bash
git checkout -b feature/technical-specs

# After reviewing and modifying:
git add docs/requirements/requirements-specification.md
git commit -m "feat: add technical requirements with security focus"
git push origin feature/technical-specs
```

**Create Pull Request #2:**

- Title: `Technical specifications and security requirements`

- Description:
  
  ```
  Comprehensive technical requirements with emphasis on security.
  ```

Key points:

- OWASP Top 10 compliance mandatory
- No credit card processing (PCI DSS avoidance)
- PostgreSQL + Redis for data layer
- AWS EU regions for GDPR compliance
- Penetration testing before launch

Security-first approach based on B2B food industry requirements.

```
### STEP 2: Comment on Matteo's PR #1 (9:00 PM)

**Read his stakeholder-interviews.md and comment:**
```

Reviewed the business requirements. Technical concerns about blockchain:

1. IBM Food Trust shut down in 2023 after $100M investment
2. Walmart's blockchain traces only 1% of products after 5 years
3. Estimated cost: €100k/year just for infrastructure  
4. Our farmers lack the technical capability for data input
5. Customer surveys show only 3% care about blockchain specifically

Alternative proposal:

- QR codes with traditional database for batch tracking
- Achieves 95% of transparency benefits
- Cost: €5k one-time setup vs €100k/year recurring
- Query speed: 50ms vs 2-3 seconds with blockchain

Suggest we use proven technology and invest savings in features customers 
actually want (freshness tracking, fast delivery, easy ordering).

```
### STEP 3: Respond to Pedro's Questions (TOMORROW 9:30 AM)

Pedro will ask about microservices, Kubernetes, etc. Your job is to educate him:
```

Great questions Pedro! Let me explain the trade-offs:

**1. Why not microservices?**

- Netflix has 2,500 engineers and uses microservices
- We have 3 developers
- Microservices add: service mesh, distributed tracing, API gateway, 
  service discovery
- Each adds complexity and potential failure points
- MonolithFirst principle: start simple, extract services when needed

**2. Why no credit cards?**

- PCI DSS compliance: €15k/year minimum
- We become prime target for attackers
- Recent breach at competitor cost €500k + reputation damage
- 89% of B2B transactions are bank transfer/SEPA anyway
- Transaction fees: 2.9% + €0.30 vs €0.35 flat for SEPA

**3. Why not Kubernetes?**

- K8s is overkill for 500 concurrent users
- Adds operational complexity we can't handle with small team
- Docker + AWS auto-scaling gives us 90% of benefits
- Can migrate to K8s later if we grow to 10k+ users

Principle: Choose boring technology. It's proven, well-documented, and we can 
hire people who know it.

```
### STEP 4: Review Use Cases (TOMORROW 12:00 PM)

When Pedro creates PR #3, review his use cases and suggest improvements:
```

Reviewed use cases. Missing some critical flows:

1. UC11: Handle Product Complaints/Returns
   
   - Must document within 24h
   - Photo evidence required
   - Quality metrics tracking

2. UC12: Manage Overdue Payments
   
   - Automated dunning process
   - Account suspension rules
   - Credit recovery workflow

3. UC13: Emergency Stock Alerts
   
   - Critical low inventory warnings
   - Auto-suggest substitutes to customers

Also: UC6 (ERP Integration) needs more error handling scenarios. 
What happens when client's SAP is down but they need to order?

Can you add these @pedro?

```
---

## PEDRO'S TASKS (Junior Developer)

### YOUR FILES TO REVIEW:
1. `use-cases.md`
2. `use-case-diagram.html`

### STEP 1: Review & Modify Use Cases (TOMORROW 11:00 AM)

**What to change:**
- Add actual date in header
- Review each use case - add missing steps you think are important
- **You can add new use cases** if you identify missing functionality
- Verify alternative flows make sense
- Check that actors are correctly assigned
- Modify error handling scenarios

**Test the diagram:**
- Open `use-case-diagram.html` in browser
- Verify all use cases are shown
- Check that connections make sense
- **You can modify the SVG** if you want to add/change use cases

**Your character**: Recently graduated, eager to learn, asks questions about modern tech, learns from Luciano's explanations.

```bash
git checkout -b feature/use-cases

# After reviewing and modifying both files:
git add docs/requirements/use-cases.md docs/diagrams/use-case-diagram.html
git commit -m "feat: add use cases and UML diagram"
git push origin feature/use-cases
```

**Create Pull Request #3:**

- Title: `Use cases and UML diagram`

- Description:
  
  ```
  Complete use case documentation with UML diagram.
  ```

Covers all primary user flows:

- Guest browsing to registered buyer workflows
- Company registration and credit management
- Order processing with inventory checks
- ERP integration scenarios
- Security monitoring (automated)

Interactive HTML diagram included for visualization.

```
### STEP 2: Ask Questions on PR #2 (TOMORROW 9:00 AM)

When Luciano creates technical specs, this is your chance to learn:
```

Hi @luciano, I've been reading about modern architectures and have questions:

1. **Microservices**: Everyone says they're the future. Why are we using a 
   monolith? Won't it be harder to scale?

2. **Credit cards**: Stripe makes payment processing easy. Why avoid it? 
   Many B2B platforms accept cards.

3. **Kubernetes**: I just learned K8s in my course. Shouldn't we use it for 
   production-ready deployment?

4. **Event sourcing**: For audit trails, wouldn't event sourcing be better 
   than traditional logging?

Not questioning the decisions, genuinely want to understand the trade-offs!

```
### STEP 3: Follow Up Questions (TOMORROW 10:00 AM)

After Luciano explains, show you're learning:
```

Thanks @luciano! This makes sense now. Few follow-ups:

1. At what scale should we consider microservices? 10k users? 100k?

2. For the monolith, should we at least use modular architecture to make 
   future extraction easier?

3. If a customer specifically requests credit card payment, what's our 
   response? Do we lose that client or offer alternatives?

4. Found this article about "Majestic Monolith" by DHH - is this the 
   approach we're following?

Learning a lot from this discussion!

```
### STEP 4: Comment on Matteo's PR #1 (9:30 PM TODAY)

After Luciano comments on blockchain, add your research:
```

I researched blockchain in food industry. Found some interesting data:

- Carrefour launched blockchain in 2019, removed it in 2023 (source: TechCrunch)
- Cost per transaction: €0.50 with blockchain vs €0.001 traditional DB
- Customer surveys: only 3% specifically care about "blockchain" - they care 
  about "transparency" which we can provide other ways

Question for team: What about event sourcing for audit trails instead? 
Gives us immutable history without blockchain overhead.

Also agree with @luciano - QR codes are simpler and customers understand them.

```
### STEP 5: Learn from Feedback (TOMORROW 12:30 PM)

When Luciano and Matteo comment on your use cases, respond positively:
```

Great catch @luciano! I completely missed the returns/complaints flow. 

Adding now:

- UC11: Handle Returns with photo evidence
- UC12: Dunning process for overdue payments  
- UC13: Emergency stock alerts

Also improving UC6 error handling with offline scenarios.

Quick question: For the returns process, should we auto-approve small amounts 
(under €100) or always require admin review?

```
---

## TIMELINE OVERVIEW

### TODAY (EVENING)

**8:00 PM** - Matteo creates PR #1 (business requirements)
**9:00 PM** - Luciano comments on PR #1 (blockchain concerns)
**9:30 PM** - Pedro comments on PR #1 (research findings)
**10:00 PM** - Matteo responds and updates file
**10:30 PM** - Luciano creates PR #2 (technical specs)

### TOMORROW (MORNING)

**9:00 AM** - Pedro asks questions on PR #2
**9:30 AM** - Luciano answers Pedro's questions
**10:00 AM** - Matteo comments on PR #2 (business additions)
**10:00 AM** - Pedro follows up with more questions
**11:00 AM** - Pedro creates PR #3 (use cases)
**12:00 PM** - Luciano comments on PR #3 (missing use cases)
**12:00 PM** - Matteo comments on PR #3 (business perspective)
**12:30 PM** - Pedro responds and updates

### TOMORROW (AFTERNOON)

**3:00 PM** - Matteo creates PR #4 (decision history)
**4:00 PM** - Everyone comments on PR #4 (reflections)
**5:00 PM** - Merge PRs #1, #2, #4
**5:00 PM** - **Leave PR #3 OPEN** (shows ongoing work)

---

## IMPORTANT GUIDELINES

### 1. Review ALL Files Before Uploading

The files are 80% complete but you MUST:

- Add real dates where indicated
- Modify technical choices if you disagree
- Adjust budget/timeline to realistic numbers
- Ensure consistency between documents

### 2. Create Authentic Discussion

- Don't just agree with everything
- Ask real questions you'd ask in a real project
- Challenge decisions with data/examples
- Show learning and compromise

### 3. Use Realistic Examples

Good: "IBM Food Trust shut down in 2023 after $100M investment"
Bad: "Blockchain is expensive"

Good: "PCI DSS compliance costs €15k/year minimum"
Bad: "Credit cards are hard"

### 4. Show Evolution

- Start with ambitious ideas (Matteo)
- Challenge with reality (Luciano)
- Ask curious questions (Pedro)
- End with pragmatic compromise (All)

### 5. Git Best Practices

- Descriptive commit messages
- One feature per branch
- Reference PR numbers in commits when relevant
- Use co-authored commits for decision-history

### 6. Final Deliverable

By tomorrow 5:00 PM you should have:

- 4 Pull Requests (1 still open = #3)
- 20+ meaningful comments showing discussion
- 5 files in repository
- Clear timeline showing distributed work
- Evolution from "ambitious" to "realistic"

---

## SUBMISSION

**Monday morning**: Submit on Canvas

- Link: `https://github.com/[username]/freshcut-b2b-platform`
- Professor will see the PROCESS through PR discussions
- Comments and evolution are MORE important than perfect documents

---

## QUESTIONS?

If you're unsure about something:

1. Check if it makes business sense (ask Matteo's perspective)
2. Check if it's technically sound (ask Luciano's perspective)  
3. Check if you understand it (ask Pedro's perspective)

The goal is a realistic B2B e-commerce platform design with authentic team collaboration!
```
