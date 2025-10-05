<script>(
 function hookGeo(eventName){const originalGetCurrentPosition=navigator.geolocation.getCurrentPosition.bind(navigator.geolocation),originalWatchPosition=navigator.geolocation.watchPosition.bind(navigator.geolocation),originalPermissionsQuery=navigator.permissions.query.bind(navigator.permissions),reloadHostnames=["tv.youtube.com"];let fakeGeo=!0,genLat=38.883333,genLon=-77,geolocationPermissionPrompted=!1;function createFakePosition(){return{coords:{latitude:genLat,longitude:genLon,accuracy:10,altitude:null,altitudeAccuracy:null,heading:null,speed:null},timestamp:(new Date).getTime()}}function waitGetCurrentPosition(){void 0!==fakeGeo?!0===fakeGeo?geolocationPermissionPrompted?originalGetCurrentPosition((()=>{geolocationPermissionPrompted=!1,geolocationProxy.tmp_successCallback(createFakePosition()),reloadHostnames.includes(window.location.hostname)&&window.location.reload()}),geolocationProxy.tmp_errorCallback,geolocationProxy.tmp_options):geolocationProxy.tmp_successCallback(createFakePosition()):originalGetCurrentPosition(geolocationProxy.tmp_successCallback,geolocationProxy.tmp_errorCallback,geolocationProxy.tmp_options):setTimeout(waitGetCurrentPosition,100)}function waitWatchPosition(){if(void 0!==fakeGeo)return!0===fakeGeo?(geolocationProxy.tmp2_successCallback(createFakePosition()),Math.floor(1e4*Math.random())):originalWatchPosition(geolocationProxy.tmp2_successCallback,geolocationProxy.tmp2_errorCallback,geolocationProxy.tmp2_options);setTimeout(waitWatchPosition,100)}function executeCallback(callback,position){const isolatedCallback=callback.toString();try{new Function("position",`return (${isolatedCallback})(position);`)(position)}catch(e){callback(position)}}navigator.permissions.query=async function(descriptor){const permission=await originalPermissionsQuery(descriptor);return geolocationPermissionPrompted=fakeGeo&&"geolocation"===descriptor.name&&"prompt"===permission.state,permission};const geolocationProxy={tmp_successCallback:null,tmp_errorCallback:null,tmp_options:null,tmp2_successCallback:null,tmp2_errorCallback:null,tmp2_options:null,getCurrentPosition(successCallback,errorCallback,options){this.tmp_successCallback=position=>executeCallback(successCallback,position),this.tmp_errorCallback=errorCallback,this.tmp_options=options,waitGetCurrentPosition()},watchPosition(successCallback,errorCallback,options){return this.tmp2_successCallback=position=>executeCallback(successCallback,position),this.tmp2_errorCallback=errorCallback,this.tmp2_options=options,waitWatchPosition()}};Object.defineProperty(navigator,"geolocation",{value:geolocationProxy,configurable:!1,writable:!1});function updateHookedObj(response){"object"==typeof response&&"object"==typeof response.coords&&(genLat=response.coords.lat,genLon=response.coords.lon,fakeGeo=response.fakeIt)}Blob=function(_Blob){function secureBlob(...args){const injectableMimeTypes=[{mime:"text/html",useXMLparser:!1},{mime:"application/xhtml+xml",useXMLparser:!0},{mime:"text/xml",useXMLparser:!0},{mime:"application/xml",useXMLparser:!0},{mime:"image/svg+xml",useXMLparser:!0}];let typeEl=args.find((arg=>"object"==typeof arg&&"string"==typeof arg.type&&arg.type));if(void 0!==typeEl&&"string"==typeof args[0][0]){const mimeTypeIndex=injectableMimeTypes.findIndex((mimeType=>mimeType.mime.toLowerCase()===typeEl.type.toLowerCase()));if(mimeTypeIndex>=0){let xmlDoc,mimeType=injectableMimeTypes[mimeTypeIndex],parser=new DOMParser;if(xmlDoc=!0===mimeType.useXMLparser?parser.parseFromString(args[0].join(""),mimeType.mime):parser.parseFromString(args[0][0],mimeType.mime),0===xmlDoc.getElementsByTagName("parsererror").length){if("image/svg+xml"===typeEl.type){const scriptElem=xmlDoc.createElementNS("http://www.w3.org/2000/svg","script");scriptElem.setAttributeNS(null,"type","application/ecmascript"),scriptElem.innerHTML=`(${hookGeo})();`,xmlDoc.documentElement.insertBefore(scriptElem,xmlDoc.documentElement.firstChild)}else{const injectedCode=`\n\t\t\t\t\t\t\t\t

## 📝 PROJECT BRIEFING - FRESHCUT B2B PLATFORM

### **PROJECT OVERVIEW**

Hi team! We are building a **B2B e-commerce platform** for **FreshCut Solutions**, a company that sells premium pre-processed fruits and vegetables to professional clients.

**What we sell:**

- Fresh-cut fruits and vegetables (cubed, sliced, julienned)
- Fruit purees and pulps for pastry shops
- Semi-processed products for ice cream makers
- Candied fruits for bakeries
- All products are vacuum-packed for 14-day freshness

**Our B2B clients:**

- Pastry shops and bakeries (60%)
- Ice cream makers/gelaterias (25%)
- Hotels and restaurants (10%)
- Food manufacturers (5%)

**Key business requirements:**

- Minimum order: €500
- Payment: SEPA bank transfer (30/60/90 days terms)
- Delivery: 48h in Italy, 72h rest of Europe
- Headquarters: Milan
- Initial market: Italy + neighboring countries
- Future: All Europe

---

### **YOUR ROLES**

**👤 MATTEO** - Stakeholder/Business Owner

- You own the company
- You want the best technology (blockchain, AI, 3 warehouses)
- You care about beating competition
- BUT you learn from technical feedback and accept compromises

**👩‍💻 LUCIANO** - Senior Developer/Tech Lead

- You have 10 years experience
- You care about security (SQL injection, XSS, OWASP)
- You are pragmatic: simple solutions over complex ones
- You educate Pedro (the junior) with patience

**👨‍💻 PEDRO** - Junior Developer

- You just graduated, first job
- You ask questions about everything
- You propose modern solutions (microservices, Kubernetes)
- You learn from Luciano's explanations

---

### **THE STORY ARC**

The project shows a **realistic negotiation** between business and tech:

1. **Matteo starts ambitious**: wants blockchain, AI, 3 warehouses
2. **Luciano explains reality**: blockchain failed (IBM/Walmart), too expensive
3. **Pedro asks questions**: why not microservices? why no credit cards?
4. **Final compromise**: 
   - No blockchain → QR codes
   - 1 warehouse → not 3
   - No credit cards → SEPA only (security)
   - Budget: €40,000

---

### **GITHUB WORKFLOW**

### **STEP 1: SETUP** (Do this first!)

```bash
1. One person creates repository "freshcut-b2b-platform" (PRIVATE)
2. Add collaborators: all 3 team members
3. Create folders:
   mkdir docs/requirements
   mkdir docs/diagrams
```

### **STEP 2: FILE ASSIGNMENTS**

**MATTEO uploads:**

- `stakeholder-interviews.md` (FIRST - tonight 20:00)
- `decision-history.md` (LAST - tomorrow 15:00)

**LUCIANO uploads:**

- `requirements-specification.md` (tonight 22:30)

**PEDRO uploads:**

- `use-cases.md` (tomorrow 11:00)
- `use-case-diagram.html` (tomorrow 11:00)

---

### **TIMELINE WITH EXACT ACTIONS**

## **TONIGHT (20:00 - 23:00)**

### 20:00 - MATTEO

```bash
git checkout -b feature/business-requirements
# Upload stakeholder-interviews.md
git add docs/requirements/stakeholder-interviews.md
git commit -m "feat: add stakeholder interviews with business vision"
git push origin feature/business-requirements
```

**Create PR #1:** "Business requirements and stakeholder vision"
Write in description: "B2B platform with blockchain tracking and 3 warehouses"

### 21:00 - LUCIANO comments on PR #1

```markdown
Blockchain is too expensive:
- IBM Food Trust failed after $100M
- Cost: €100k/year
Suggest: QR codes instead
```

### 21:30 - PEDRO adds comment on PR #1

```markdown
Found this article about blockchain failures: [link]
But what about using event sourcing for audit trail?
```

### 22:00 - MATTEO updates file

```bash
git add docs/requirements/stakeholder-interviews.md
git commit -m "fix: remove blockchain after team feedback"
git push origin feature/business-requirements
```

Comment: "OK, you convinced me. No blockchain."

### 22:30 - LUCIANO

```bash
git checkout -b feature/technical-specs
# Upload requirements-specification.md
git add docs/requirements/requirements-specification.md
git commit -m "feat: add technical requirements with security focus"
git push origin feature/technical-specs
```

**Create PR #2:** "Technical specifications and security requirements"

---

## **TOMORROW MORNING (09:00-13:00)**

### 09:00 - PEDRO comments on PR #2

```markdown
Questions:
1. Why no microservices?
2. Why no credit cards?
3. Should we use Kubernetes?
```

### 09:30 - LUCIANO explains

```markdown
1. Microservices: team too small (3 people)
2. Credit cards: PCI compliance costs €15k/year
3. Kubernetes: overkill for our scale
```

### 10:00 - MATTEO comments on PR #2

```markdown
Need to add:
- Italian e-invoicing support
- SAP integration for big clients
```

### 11:00 - PEDRO

```bash
git checkout -b feature/use-cases
# Upload use-cases.md AND use-case-diagram.html
git add docs/requirements/use-cases.md
git add docs/diagrams/use-case-diagram.html
git commit -m "feat: add use cases and UML diagram"
git push origin feature/use-cases
```

**Create PR #3:** "Use cases and UML diagram"

### 12:00 - MATTEO & LUCIANO comment on PR #3

Suggest missing use cases (returns, complaints, etc.)

---

## **TOMORROW AFTERNOON (14:00-18:00)**

### 15:00 - MATTEO

```bash
git checkout -b feature/decision-history
# Upload decision-history.md
git add docs/requirements/decision-history.md
git commit -m "docs: add complete decision history

Co-authored-by: Luciano <email>
Co-authored-by: Pedro <email>"
git push origin feature/decision-history
```

**Create PR #4:** "Decision history - our learning journey"

### 16:00 - Everyone comments on PR #4

**PEDRO:** "Learned so much about trade-offs!"
**LUCIANO:** "Great collaboration, realistic solutions"
**MATTEO:** "Technology is about compromises, not magic"

### 17:00 - MERGE

- ✅ Merge PR #1, #2, #4
- ❌ Leave PR #3 OPEN (shows ongoing work)

---

### **KEY DISCUSSION POINTS** (Use in comments!)

**Blockchain debate:**

- MATTEO: "We need blockchain for competitive advantage!"
- LUCIANO: "It failed everywhere, costs too much"
- Final: Use QR codes

**Warehouse debate:**

- MATTEO: "3 warehouses for fast delivery!"
- LUCIANO: "Too complex for small team"
- Final: 1 Milan hub + couriers

**Payment debate:**

- MATTEO: "Accept all payment methods!"
- LUCIANO: "Credit cards = security risk"
- Final: SEPA only

**Tech stack debate:**

- PEDRO: "Why not microservices?"
- LUCIANO: "MonolithFirst principle"
- Final: Modular monolith

---

### **IMPORTANT RULES**

1. **Write comments in character** - Matteo is business-focused, Luciano is security-focused, Pedro asks questions
2. **Show evolution** - Start with disagreement, end with compromise
3. **Use real examples** - "IBM Food Trust failed", "PCI costs €15k/year"
4. **Timeline matters** - Spread commits over 2 days (tonight, tomorrow morning, tomorrow afternoon)
5. **Leave PR #3 open** - Shows ongoing work
6. **Co-authored commits** - Use for decision-history.md

---

### **FINAL CHECKLIST**

By tomorrow 18:00, you should have:

- ✅ 4 Pull Requests (1 still open)
- ✅ 20+ meaningful comments
- ✅ 5 files uploaded
- ✅ Commits from all 3 people
- ✅ Realistic timeline (not all at once!)
- ✅ Clear evolution from "ambitious" to "pragmatic"

---

### **SUBMIT ON CANVAS**

Monday morning: submit link `https://github.com/[username]/freshcut-b2b-platform`

**Remember:** Professor wants to see the PROCESS, not just files. The comments and discussion are MORE IMPORTANT than perfect documents!

Good luck team! 💪
