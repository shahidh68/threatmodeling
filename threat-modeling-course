import { useState } from "react";

const course = {
  modules: [
    {
      id: 1,
      title: "What Is Threat Modeling?",
      icon: "🧠",
      color: "#00D4FF",
      theory: `Threat modeling is a structured way of thinking about risk. Rather than waiting for something bad to happen, you proactively ask: **What could go wrong? Who might cause it? How likely is it? What's the impact?**

It's used by security professionals, engineers, investors, military strategists, product managers — and anyone who needs to make decisions under uncertainty.

**The Core Questions (STRIDE framework origin)**
Every threat model starts with four questions:
1. **What are we building/protecting?** (Assets & system boundaries)
2. **What can go wrong?** (Threat identification)
3. **What do we do about it?** (Mitigations & controls)
4. **Did we do a good job?** (Validation & review)

**Why it matters:** Without threat modeling, you protect against what's *visible* — not what's *likely*. You build locks on front doors while leaving windows open.`,
      keyTerms: [
        { term: "Asset", def: "Anything of value worth protecting — data, money, reputation, property, life." },
        { term: "Threat", def: "A potential event that could cause harm to an asset." },
        { term: "Threat Actor", def: "The person or entity who might carry out the threat." },
        { term: "Vulnerability", def: "A weakness that a threat actor could exploit." },
        { term: "Risk", def: "Likelihood × Impact. A threat you're exposed to through a vulnerability." },
        { term: "Mitigation", def: "A control or action that reduces risk — either likelihood or impact." },
        { term: "Attack Surface", def: "All the possible entry points through which an attacker could try to cause harm." },
      ],
      scenario: null,
    },
    {
      id: 2,
      title: "Identifying Assets",
      icon: "💎",
      color: "#FFD700",
      theory: `Before you can protect anything, you must know **what you're protecting** and **why it matters**.

Assets aren't always obvious. Think in categories:

**Tangible assets:** Money, property, physical objects, equipment
**Intangible assets:** Reputation, relationships, data, intellectual property, time
**Process assets:** Systems, workflows, supply chains, access credentials
**Human assets:** People, their skills, their safety

**The key discipline:** rank assets by value. You cannot protect everything equally — resources are finite. Threat modeling forces prioritisation.

**Asset mapping tip:** Ask "If this was gone or compromised tomorrow, what's the worst that happens?" The answer tells you how much it's worth protecting.`,
      keyTerms: [
        { term: "Crown Jewels", def: "The most critical, high-value assets that absolutely must be protected." },
        { term: "Data Classification", def: "Categorising information by sensitivity: public, internal, confidential, secret." },
        { term: "Single Point of Failure", def: "An asset whose compromise would cause catastrophic cascading damage." },
      ],
      scenario: {
        title: "Scenario: The Small Business Owner",
        description: "Priya runs a physiotherapy clinic in Birmingham. She has 3 staff, 400 patients, an appointment booking system, and a good local reputation. She's heard about cyber attacks and wants to start threat modeling.",
        question: "Which of these are her MOST critical assets to protect?",
        options: [
          { text: "Her clinic's social media follower count", correct: false, feedback: "Low value — followers can be rebuilt. This is a secondary asset at best." },
          { text: "Patient health records and personal data", correct: true, feedback: "Correct! Patient data is a crown jewel — legally protected (GDPR), sensitive, and a core trust asset. Breach = fines, reputational damage, patient harm." },
          { text: "Her appointment booking software login", correct: true, feedback: "Correct! Access credentials are a gateway asset. Whoever controls them controls the business operations. Often underestimated." },
          { text: "The Wi-Fi router password written on a sticky note", correct: true, feedback: "Correct! This is a classic access control failure. Network access = access to everything behind it. The sticky note is the vulnerability." },
        ],
        multiSelect: true,
      },
    },
    {
      id: 3,
      title: "Identifying Threat Actors",
      icon: "🎭",
      color: "#FF6B6B",
      theory: `Threats don't come from nowhere — they come from **actors** with **motivation**, **capability**, and **opportunity**.

**The Threat Actor Spectrum:**

🔴 **Nation-states** — Sophisticated, well-resourced, patient. Motivated by geopolitics, espionage, disruption.
🟠 **Organised crime** — Financially motivated. Ransomware, fraud, data theft.
🟡 **Hacktivists** — Ideologically motivated. Reputational damage, disruption, leaks.
🟢 **Insiders** — Employees, contractors, ex-staff. Motivated by grievance, money, negligence.
🔵 **Opportunists** — Unsophisticated attackers exploiting easy targets. Low skill, high volume.
⚪ **Competitors** — Industrial espionage, talent poaching, market manipulation.

**The key insight:** You don't need to defend against *all* actors equally. A small bakery doesn't need to defend against nation-states. A nuclear facility does. Match your defences to your realistic threat actor profile.

**Motivation + Capability + Opportunity = Risk**
Remove any one element and the risk collapses.`,
      keyTerms: [
        { term: "Threat Actor Profile", def: "A description of who might attack you, why, and with what capability." },
        { term: "TTPs", def: "Tactics, Techniques, and Procedures — how a threat actor operates." },
        { term: "Insider Threat", def: "Risk from people with legitimate access who misuse it, intentionally or accidentally." },
        { term: "APT", def: "Advanced Persistent Threat — a sophisticated, long-term targeted attack, usually state-sponsored." },
      ],
      scenario: {
        title: "Scenario: The Property Developer",
        description: "You're an overseas Pakistani investor who just purchased an off-plan apartment in Islamabad for £60,000. You've wired the money to the developer and are awaiting construction updates.",
        question: "Which threat actors pose the most realistic risk to YOUR investment specifically?",
        options: [
          { text: "Nation-state hackers targeting you personally", correct: false, feedback: "Very unlikely for a private individual investor. Nation-states target governments, infrastructure, and strategic assets — not individual property buyers." },
          { text: "The developer becoming financially insolvent", correct: true, feedback: "Correct! Financial failure of the developer is one of the highest probability risks in off-plan property. This is an 'insider' systemic threat — people with your money who may not be able to deliver." },
          { text: "Opportunistic fraud by a local agent misrepresenting the project", correct: true, feedback: "Correct! This is a classic high-frequency threat in Pakistan's property market. Agents and middlemen are motivated by commission and may misrepresent, over-promise, or outright defraud." },
          { text: "Political instability affecting DHA land rights", correct: true, feedback: "Correct! While DHA has strong institutional protections, geopolitical events or government policy changes are legitimate systemic risks that could freeze or impair your asset." },
        ],
        multiSelect: true,
      },
    },
    {
      id: 4,
      title: "The STRIDE Framework",
      icon: "⚔️",
      color: "#A855F7",
      theory: `STRIDE is a systematic way to categorise threats, originally developed by Microsoft for software security but applicable to almost any domain.

**S — Spoofing**
Pretending to be something/someone you're not.
*"I'm from your bank calling about a suspicious transaction..."*

**T — Tampering**
Modifying data, systems, or processes without authorisation.
*Altering a land registry document. Changing contract terms after signing.*

**R — Repudiation**
Denying that something happened when it did.
*"I never received that payment." "I never agreed to those terms."*

**I — Information Disclosure**
Exposing information to people who shouldn't have it.
*Leaking patient records. Publishing confidential financials.*

**D — Denial of Service**
Preventing legitimate use of a system or resource.
*Blocking access to your funds. Locking you out of your accounts.*

**E — Elevation of Privilege**
Gaining access or power beyond what you're authorised for.
*An employee accessing director-level financial records. A contractor gaining admin rights.*

**Using STRIDE:** For each asset, systematically ask: Can it be spoofed? Tampered with? Repudiated? Disclosed? Denied? Escalated?`,
      keyTerms: [
        { term: "Spoofing", def: "Impersonating a legitimate entity to gain trust or access." },
        { term: "Tampering", def: "Unauthorised modification of data, code, or systems." },
        { term: "Repudiation", def: "Denying accountability for an action — 'it wasn't me'." },
        { term: "Information Disclosure", def: "Unauthorised exposure of sensitive data." },
        { term: "Denial of Service", def: "Blocking legitimate access to resources or services." },
        { term: "Elevation of Privilege", def: "Gaining unauthorised levels of access or authority." },
      ],
      scenario: {
        title: "Scenario: The Job Offer",
        description: "Alex receives a LinkedIn message from a 'Senior Recruiter at Goldman Sachs' offering a role with a £20k salary increase. The recruiter asks Alex to complete an assessment on an external link and share his current payslips and passport scan to 'begin the screening process'.",
        question: "Which STRIDE categories apply to this threat?",
        options: [
          { text: "Spoofing — the 'recruiter' may not be from Goldman Sachs at all", correct: true, feedback: "Correct! This is a textbook spoofing attack — impersonating a trusted brand (Goldman Sachs) to gain Alex's confidence and compliance." },
          { text: "Denial of Service — they want to block Alex from applying elsewhere", correct: false, feedback: "Not really applicable here. DoS is about blocking access to systems/resources, not competitive interference in job applications." },
          { text: "Information Disclosure — requesting passport and payslips", correct: true, feedback: "Correct! Asking for identity documents and financial data is an attempt to harvest sensitive personal information — a classic phishing/social engineering play." },
          { text: "Tampering — the external assessment link may install malware", correct: true, feedback: "Correct! External links in phishing attacks often deliver malware that can tamper with the victim's device, steal credentials, or compromise systems." },
        ],
        multiSelect: true,
      },
    },
    {
      id: 5,
      title: "Risk Scoring: Likelihood × Impact",
      icon: "📊",
      color: "#10B981",
      theory: `Not all risks are equal. Risk scoring lets you **prioritise** where to spend your time, money, and attention.

**The Basic Formula:**
Risk Score = Likelihood × Impact

Rate each on a scale of 1–5:
- **Likelihood:** How probable is this threat? (1=rare, 5=almost certain)
- **Impact:** How bad would it be? (1=minor inconvenience, 5=catastrophic/existential)

**Risk Matrix:**

| | Low Impact | Medium Impact | High Impact |
|---|---|---|---|
| **High Likelihood** | Medium Risk | High Risk | 🔴 Critical |
| **Medium Likelihood** | Low Risk | Medium Risk | High Risk |
| **Low Likelihood** | Negligible | Low Risk | Medium Risk |

**DREAD model** (extended scoring):
- **D**amage potential
- **R**eproducibility (how easy to repeat)
- **E**xploitability (how easy to execute)
- **A**ffected users
- **D**iscoverability (how findable is the vulnerability)

**Key insight:** High-likelihood, low-impact risks are annoying. Low-likelihood, high-impact risks are catastrophic. Your mitigation strategy differs drastically for each.`,
      keyTerms: [
        { term: "Risk Appetite", def: "How much risk an organisation or individual is willing to accept." },
        { term: "Risk Tolerance", def: "The acceptable deviation from risk appetite before action is required." },
        { term: "Residual Risk", def: "The risk that remains after controls and mitigations are applied." },
        { term: "Risk Register", def: "A documented list of identified risks, their scores, owners, and mitigations." },
      ],
      scenario: {
        title: "Scenario: Rate These Risks",
        description: "You run a small e-commerce business selling handmade goods online. Score each risk and decide which to prioritise first.",
        question: "Which risk should you tackle FIRST based on Likelihood × Impact?",
        options: [
          { text: "A nation-state hacking your Etsy shop (L:1, I:3)", correct: false, feedback: "Score: 3. Very low likelihood means this isn't a priority despite moderate impact. Don't build a bunker for your craft shop." },
          { text: "A customer disputing a transaction and getting a chargeback (L:4, I:2)", correct: false, feedback: "Score: 8. Real risk, but impact is manageable — individual transaction losses. Important but not first priority." },
          { text: "Your payment processor account being suspended due to fraud flags (L:2, I:5)", correct: false, feedback: "Score: 10. High impact (can't take payments = business stops) but lower likelihood. Important to have a backup plan." },
          { text: "Losing access to your email account which controls all logins (L:3, I:5)", correct: true, feedback: "Score: 15. Correct! Your email is the 'master key' to everything. Medium-high likelihood (password reuse, phishing) × catastrophic impact = highest priority. Enable 2FA immediately." },
        ],
        multiSelect: false,
      },
    },
    {
      id: 6,
      title: "Mitigations & Controls",
      icon: "🛡️",
      color: "#F59E0B",
      theory: `Once you've identified and scored threats, you choose how to respond. There are **four strategic responses** to any risk:

**1. AVOID** — Eliminate the activity that creates the risk entirely.
*Don't store customer data you don't need. Don't take that flight.*

**2. MITIGATE** — Reduce the likelihood or impact through controls.
*Add two-factor authentication. Install smoke detectors. Build contractual protections.*

**3. TRANSFER** — Shift the financial consequence to another party.
*Buy insurance. Contractual indemnities. Outsource the risky process.*

**4. ACCEPT** — Acknowledge the risk and live with it (consciously).
*This is valid for low-score risks. The key word is *consciously* — not just ignoring it.*

**Types of Controls:**
- **Preventive** — Stop the threat from occurring (locks, encryption, background checks)
- **Detective** — Identify when a threat has occurred (alarms, monitoring, audits)
- **Corrective** — Reduce damage after the fact (backups, incident response, insurance)
- **Deterrent** — Discourage threat actors (visible cameras, legal disclaimers, reputation)

**The Defence-in-Depth principle:** Layer multiple controls. If one fails, others catch it. No single control is perfect — this is why Swiss cheese model failures happen: holes align.`,
      keyTerms: [
        { term: "Defence in Depth", def: "Using multiple layered controls so no single failure creates catastrophic exposure." },
        { term: "Principle of Least Privilege", def: "Give users/systems only the minimum access they need — nothing more." },
        { term: "Zero Trust", def: "Never assume anything inside or outside your network is safe. Verify everything." },
        { term: "Compensating Control", def: "An alternative control used when the standard one isn't feasible." },
      ],
      scenario: {
        title: "Scenario: The Landlord's Dilemma",
        description: "James owns a rental property. His tenant has just vacated, and he's worried about several risks before getting a new tenant: the property sitting empty, squatters, a burst pipe going unnoticed, and choosing a bad next tenant.",
        question: "Match the right mitigation strategy to the squatter risk specifically:",
        options: [
          { text: "Accept the risk — squatters are very rare", correct: false, feedback: "Accepting works for LOW-score risks. Squatters can cause significant legal and financial damage (eviction is expensive and slow in the UK) — this risk warrants active mitigation." },
          { text: "Mitigate — install timer lights, use a property management company to check weekly, and secure all entry points", correct: true, feedback: "Correct! This is layered mitigation: deterrence (lights suggesting occupancy) + detective control (regular checks) + preventive control (securing entry). Classic defence in depth." },
          { text: "Transfer — buy landlord insurance and let the insurer deal with it", correct: false, feedback: "Insurance rarely covers squatter removal costs comprehensively. Transfer is not the primary strategy here — it might be a secondary layer, but squatter prevention requires direct mitigations." },
          { text: "Avoid — sell the property so you never have this risk", correct: false, feedback: "Technically valid (avoidance eliminates the risk) but wildly disproportionate to the threat. Avoidance is for when the risk is structural and unavoidable — not for a manageable property security issue." },
        ],
        multiSelect: false,
      },
    },
    {
      id: 7,
      title: "Attack Trees",
      icon: "🌳",
      color: "#06B6D4",
      theory: `An **attack tree** is a visual, hierarchical way to map out how a threat actor might achieve their goal. It shows the *paths* to an attack, not just the attack itself.

**Structure:**
- **Root node** = The attacker's ultimate goal
- **Child nodes** = Sub-goals or steps needed to achieve the parent
- **Leaf nodes** = Specific, concrete actions the attacker takes
- **AND nodes** = All children must succeed for parent to succeed
- **OR nodes** = Any one child succeeding achieves the parent goal

**Example: Attacker goal = "Steal money from a business bank account"**

Root: Steal funds
├── OR: Compromise online banking login
│   ├── OR: Phish credentials via fake email
│   ├── OR: Buy stolen credentials on dark web
│   └── AND: Install keylogger + wait for victim to log in
├── OR: Social engineer bank into transferring funds
│   ├── AND: Spoof CEO email + target Finance team
│   └── AND: Create urgency (fake emergency)
└── OR: Compromise accounting software
    └── AND: Exploit software vulnerability + redirect payments

**Why attack trees are powerful:** They show you WHERE to invest in defences. If you cut off a high-probability branch near the root, you stop many attacks at once. If leaf nodes are all expensive/difficult, the overall risk is lower.`,
      keyTerms: [
        { term: "Attack Vector", def: "The path or method used by an attacker to gain access." },
        { term: "Attack Path", def: "The specific sequence of steps from initial access to the final goal." },
        { term: "Root Cause", def: "The underlying vulnerability or weakness that enables an attack path." },
        { term: "Choke Point", def: "A single control that blocks multiple attack paths simultaneously." },
      ],
      scenario: {
        title: "Scenario: Build the Attack Tree",
        description: "A fraudster wants to impersonate you and take control of your mobile number (SIM swap attack) to intercept 2FA codes and drain your crypto wallet.",
        question: "Which step is the most critical CHOKE POINT to defend against this attack?",
        options: [
          { text: "Protect your crypto wallet with a strong password", correct: false, feedback: "Useful, but the attacker isn't targeting your wallet password directly — they're targeting your phone number to intercept SMS 2FA codes. A strong wallet password doesn't stop SIM swap." },
          { text: "Use an authenticator app (not SMS) for 2FA on financial accounts", correct: true, feedback: "Correct! This is the most powerful choke point. If 2FA codes go to an app on your device (not SMS), a SIM swap gives the attacker nothing useful. You've cut the attack tree at its root." },
          { text: "Use a different mobile network", correct: false, feedback: "SIM swap attacks work across all UK mobile networks — the vulnerability is in social engineering customer service, not the network itself. Switching networks doesn't address the root vulnerability." },
          { text: "Enable a SIM lock/PIN with your mobile carrier", correct: true, feedback: "Also correct! A SIM PIN/lock adds friction at the carrier level — making it much harder for an attacker to convince customer service to transfer your number. This is a preventive control at the attack entry point." },
        ],
        multiSelect: true,
      },
    },
    {
      id: 8,
      title: "Real-World Application: Geopolitical Threat Modeling",
      icon: "🌍",
      color: "#EF4444",
      theory: `Threat modeling isn't just for cybersecurity — it's the same mental framework used by intelligence analysts, military strategists, and geopolitical risk consultants.

**Applying threat modeling to country/investment risk:**

**Assets:** Your capital, your property rights, your ability to repatriate funds, your physical safety
**Threat actors:** Hostile governments, criminal networks, corrupt officials, unstable institutions
**Vulnerabilities:** Weak rule of law, currency controls, nuclear flashpoints, political instability

**The PESTLE Framework** (macro threat scan):
- **P**olitical — Government stability, election risk, military influence
- **E**conomic — Currency risk, inflation, debt default, capital controls
- **S**ocial — Civil unrest, sectarianism, crime rates
- **T**echnological — Infrastructure resilience, cyber capability
- **L**egal — Rule of law, property rights, contract enforcement
- **E**nvironmental — Natural disasters, climate risk

**Key geopolitical threat modeling tools:**
- **Scenario planning** — Map out 3-5 plausible futures (best, base, worst case)
- **Red teaming** — Have someone argue the bear case as forcefully as possible
- **Black swan identification** — What low-probability, high-impact events could occur?
- **Tripwire setting** — Define the early warning signals that would trigger your exit plan`,
      keyTerms: [
        { term: "Black Swan", def: "A rare, high-impact, previously inconceivable event (Nassim Taleb). Usually obvious in retrospect." },
        { term: "Scenario Planning", def: "Developing detailed narratives of plausible future states to stress-test decisions." },
        { term: "Red Teaming", def: "Assigning a team to attack your own assumptions and find weaknesses in your plan." },
        { term: "Tripwire", def: "A pre-defined signal or threshold that, when triggered, automatically initiates a response plan." },
      ],
      scenario: {
        title: "Scenario: Pakistan Investment Tripwires",
        description: "You've invested £60,000 in off-plan property in Islamabad. You want to set tripwires — early warning signals — that would prompt you to investigate or accelerate your exit.",
        question: "Which of these would be the most meaningful TRIPWIRES to monitor?",
        options: [
          { text: "Pakistan drops out of the top 50 on the Global Peace Index", correct: false, feedback: "Too lagging and too broad. The GPI is published annually and reflects historical events — by the time it moves, you'd already be aware of the underlying events through faster indicators." },
          { text: "IMF suspends Pakistan's loan programme or Pakistan misses a debt payment", correct: true, feedback: "Correct! This is a fast-moving, high-signal tripwire. IMF suspension = financial system under acute stress = capital flight risk, currency collapse, and frozen asset markets. Time to act." },
          { text: "The developer misses a construction milestone or goes quiet on communications", correct: true, feedback: "Correct! Developer-specific tripwires are essential for off-plan risk. Missed milestones, unreturned calls, or changed payment instructions are early fraud/insolvency signals. Investigate immediately." },
          { text: "A military skirmish or elevated tension on the India-Pakistan border", correct: true, feedback: "Correct! Even short of full war, military escalation triggers capital flight, currency depreciation, and foreign investment freezes. Monitoring border tension is a key geopolitical tripwire for Pakistan assets." },
        ],
        multiSelect: true,
      },
    },
    {
      id: 9,
      title: "The Threat Modeling Process End-to-End",
      icon: "🔄",
      color: "#8B5CF6",
      theory: `Now you bring it all together. A complete threat model follows this cycle:

**Step 1: Define scope & objectives**
What are you protecting? What's the time horizon? What's your risk appetite?

**Step 2: Asset inventory**
List and rank all assets. Identify crown jewels.

**Step 3: System/context mapping**
Understand boundaries, data flows, trust relationships, and dependencies.

**Step 4: Threat enumeration**
Use STRIDE, attack trees, and threat actor profiling to systematically identify threats.

**Step 5: Risk scoring**
Likelihood × Impact for each threat. Build a risk register.

**Step 6: Mitigation planning**
For each high-priority risk: Avoid, Mitigate, Transfer, or Accept. Assign owners.

**Step 7: Residual risk review**
After mitigations: what risk remains? Is it within appetite?

**Step 8: Monitor & iterate**
Threat models go stale. Set tripwires. Review on schedule (quarterly, annually, after major changes).

**The key mindset shift:** Threat modeling is not about achieving zero risk. It's about making **conscious, informed decisions** about which risks to carry and which to eliminate. The goal is to be surprised as rarely as possible — and to have a plan when you are.`,
      keyTerms: [
        { term: "Threat Model", def: "A structured document or process capturing assets, threats, risks, and mitigations for a system." },
        { term: "Review Cadence", def: "The scheduled frequency at which a threat model is revisited and updated." },
        { term: "Risk Register", def: "A living document that tracks all identified risks, their scores, owners, status, and mitigations." },
        { term: "Security Posture", def: "The overall strength of an organisation's defences across people, process, and technology." },
      ],
      scenario: {
        title: "Final Scenario: Your Own Life",
        description: "Apply threat modeling to yourself. You're a professional in your 30s or 40s. You have savings, a career, a family, and a digital life. What does YOUR personal threat model look like?",
        question: "Which area represents the HIGHEST residual risk for most people (i.e., the one most people ignore despite high likelihood × impact)?",
        options: [
          { text: "Physical home security (burglary)", correct: false, feedback: "Most people actually *do* address this — they have locks, contents insurance, maybe alarms. Residual risk here is relatively low because it's visible and culturally normalised to protect against." },
          { text: "Identity theft and account takeover", correct: true, feedback: "Correct! This is the classic high-residual-risk blind spot. Likelihood is very high (billions of credentials circulate online), impact is severe (financial loss, credit damage, years of recovery), yet most people still reuse passwords and use SMS 2FA. Enormous gap between risk and mitigation." },
          { text: "Long-term illness or disability affecting income", correct: false, feedback: "High impact, but most people with mortgages or families are nudged toward income protection insurance by advisors. Residual risk varies but is often lower than digital identity risk in practice." },
          { text: "Reputational damage from social media", correct: false, feedback: "A real risk, but most people aren't targeted, and the impact is usually manageable. Not the highest-residual gap for the average professional." },
        ],
        multiSelect: false,
      },
    },
  ],
};

export default function ThreatModelingCourse() {
  const [currentModule, setCurrentModule] = useState(0);
  const [tab, setTab] = useState("learn");
  const [selected, setSelected] = useState([]);
  const [submitted, setSubmitted] = useState(false);
  const [completedModules, setCompletedModules] = useState(new Set());
  const [showGlossary, setShowGlossary] = useState(false);

  const mod = course.modules[currentModule];

  const handleSelect = (idx) => {
    if (submitted) return;
    if (mod.scenario?.multiSelect) {
      setSelected((s) => s.includes(idx) ? s.filter((i) => i !== idx) : [...s, idx]);
    } else {
      setSelected([idx]);
    }
  };

  const handleSubmit = () => {
    if (selected.length === 0) return;
    setSubmitted(true);
    setCompletedModules((prev) => new Set([...prev, currentModule]));
  };

  const goToModule = (idx) => {
    setCurrentModule(idx);
    setTab("learn");
    setSelected([]);
    setSubmitted(false);
  };

  const nextModule = () => {
    if (currentModule < course.modules.length - 1) {
      goToModule(currentModule + 1);
    }
  };

  const progress = Math.round((completedModules.size / course.modules.length) * 100);

  const renderTheory = (text) => {
    return text.split('\n').map((line, i) => {
      if (line.startsWith('**') && line.endsWith('**')) {
        return <h3 key={i} style={{ color: mod.color, fontFamily: "'Syne', sans-serif", fontSize: '1rem', marginTop: '1.2rem', marginBottom: '0.3rem' }}>{line.replace(/\*\*/g, '')}</h3>;
      }
      if (line.match(/^\*\*.*\*\*/)) {
        const parts = line.split(/(\*\*[^*]+\*\*)/g);
        return <p key={i} style={{ marginBottom: '0.5rem', lineHeight: 1.7 }}>{parts.map((p, j) => p.startsWith('**') ? <strong key={j} style={{ color: '#e2e8f0' }}>{p.replace(/\*\*/g, '')}</strong> : p)}</p>;
      }
      if (line.startsWith('- ')) {
        return <li key={i} style={{ marginLeft: '1rem', marginBottom: '0.3rem', lineHeight: 1.6 }}>{line.slice(2).split(/(\*\*[^*]+\*\*)/g).map((p, j) => p.startsWith('**') ? <strong key={j} style={{ color: '#e2e8f0' }}>{p.replace(/\*\*/g, '')}</strong> : p)}</li>;
      }
      if (line.startsWith('🔴') || line.startsWith('🟠') || line.startsWith('🟡') || line.startsWith('🟢') || line.startsWith('🔵') || line.startsWith('⚪')) {
        const parts = line.split(/(\*\*[^*]+\*\*)/g);
        return <p key={i} style={{ marginBottom: '0.4rem', lineHeight: 1.6 }}>{parts.map((p, j) => p.startsWith('**') ? <strong key={j} style={{ color: mod.color }}>{p.replace(/\*\*/g, '')}</strong> : p)}</p>;
      }
      if (line.trim() === '') return <br key={i} />;
      const parts = line.split(/(\*\*[^*]+\*\*)/g);
      return <p key={i} style={{ marginBottom: '0.5rem', lineHeight: 1.7 }}>{parts.map((p, j) => p.startsWith('**') ? <strong key={j} style={{ color: '#e2e8f0' }}>{p.replace(/\*\*/g, '')}</strong> : p)}</p>;
    });
  };

  const allCorrect = mod.scenario && submitted && selected.every(i => mod.scenario.options[i].correct) && mod.scenario.options.filter(o => o.correct).length === selected.length;

  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=IBM+Plex+Mono:wght@400;500&family=Inter:wght@300;400;500&display=swap');
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background: #080c14; }
        ::-webkit-scrollbar { width: 4px; }
        ::-webkit-scrollbar-track { background: #0f1624; }
        ::-webkit-scrollbar-thumb { background: #2a3550; border-radius: 2px; }
        .module-btn:hover { transform: translateX(4px); }
        .option-btn:hover { border-color: rgba(255,255,255,0.3) !important; }
        .tab-btn:hover { opacity: 0.8; }
      `}</style>

      <div style={{ display: 'flex', height: '100vh', background: '#080c14', fontFamily: "'Inter', sans-serif", color: '#94a3b8', overflow: 'hidden' }}>

        {/* Sidebar */}
        <div style={{ width: '260px', minWidth: '260px', background: '#0d1526', borderRight: '1px solid #1e2d47', display: 'flex', flexDirection: 'column', overflow: 'hidden' }}>
          {/* Logo */}
          <div style={{ padding: '1.5rem 1.2rem 1rem', borderBottom: '1px solid #1e2d47' }}>
            <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 800, fontSize: '1.1rem', color: '#e2e8f0', letterSpacing: '-0.02em' }}>
              THREAT<span style={{ color: '#00D4FF' }}>MODEL</span>
            </div>
            <div style={{ fontSize: '0.7rem', color: '#475569', marginTop: '0.2rem', fontFamily: "'IBM Plex Mono', monospace" }}>v1.0 — LEARNING SYSTEM</div>
            <div style={{ marginTop: '1rem' }}>
              <div style={{ display: 'flex', justifyContent: 'space-between', fontSize: '0.7rem', color: '#64748b', marginBottom: '0.4rem' }}>
                <span>PROGRESS</span>
                <span style={{ color: '#00D4FF', fontFamily: "'IBM Plex Mono', monospace" }}>{progress}%</span>
              </div>
              <div style={{ height: '3px', background: '#1e2d47', borderRadius: '2px' }}>
                <div style={{ height: '100%', width: `${progress}%`, background: `linear-gradient(90deg, #00D4FF, #8B5CF6)`, borderRadius: '2px', transition: 'width 0.5s ease' }} />
              </div>
            </div>
          </div>

          {/* Module list */}
          <div style={{ flex: 1, overflowY: 'auto', padding: '0.8rem 0.6rem' }}>
            {course.modules.map((m, i) => (
              <button
                key={m.id}
                onClick={() => goToModule(i)}
                className="module-btn"
                style={{
                  width: '100%', textAlign: 'left', background: i === currentModule ? `${m.color}18` : 'transparent',
                  border: `1px solid ${i === currentModule ? m.color + '44' : 'transparent'}`,
                  borderRadius: '8px', padding: '0.6rem 0.8rem', cursor: 'pointer', marginBottom: '0.3rem',
                  transition: 'all 0.15s ease', display: 'flex', alignItems: 'center', gap: '0.6rem'
                }}
              >
                <span style={{ fontSize: '1rem', opacity: i === currentModule ? 1 : 0.7 }}>{m.icon}</span>
                <div style={{ flex: 1, minWidth: 0 }}>
                  <div style={{ fontSize: '0.72rem', fontWeight: 600, color: i === currentModule ? m.color : '#64748b', fontFamily: "'Syne', sans-serif", whiteSpace: 'nowrap', overflow: 'hidden', textOverflow: 'ellipsis' }}>
                    {m.title}
                  </div>
                  <div style={{ fontSize: '0.62rem', color: '#334155', fontFamily: "'IBM Plex Mono', monospace" }}>Module {m.id}</div>
                </div>
                {completedModules.has(i) && <span style={{ color: '#10B981', fontSize: '0.8rem' }}>✓</span>}
              </button>
            ))}
          </div>

          <div style={{ padding: '0.8rem', borderTop: '1px solid #1e2d47' }}>
            <button
              onClick={() => setShowGlossary(!showGlossary)}
              style={{ width: '100%', background: '#1e2d47', border: '1px solid #2a3f5f', borderRadius: '6px', padding: '0.5rem', color: '#64748b', fontSize: '0.72rem', cursor: 'pointer', fontFamily: "'IBM Plex Mono', monospace' " }}
            >
              📖 {showGlossary ? 'HIDE' : 'SHOW'} GLOSSARY
            </button>
          </div>
        </div>

        {/* Main content */}
        <div style={{ flex: 1, display: 'flex', flexDirection: 'column', overflow: 'hidden' }}>
          {/* Header */}
          <div style={{ padding: '1.2rem 2rem', borderBottom: '1px solid #1e2d47', display: 'flex', alignItems: 'center', gap: '1rem', background: '#0a1120' }}>
            <div style={{ width: '40px', height: '40px', borderRadius: '10px', background: `${mod.color}22`, border: `1px solid ${mod.color}55`, display: 'flex', alignItems: 'center', justifyContent: 'center', fontSize: '1.3rem' }}>
              {mod.icon}
            </div>
            <div>
              <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 700, fontSize: '1.15rem', color: '#e2e8f0' }}>{mod.title}</div>
              <div style={{ fontSize: '0.72rem', color: '#475569', fontFamily: "'IBM Plex Mono', monospace" }}>MODULE {mod.id} OF {course.modules.length}</div>
            </div>
            <div style={{ marginLeft: 'auto', display: 'flex', gap: '0.5rem' }}>
              {['learn', mod.scenario ? 'scenario' : null, 'terms'].filter(Boolean).map(t => (
                <button
                  key={t}
                  onClick={() => setTab(t)}
                  className="tab-btn"
                  style={{
                    background: tab === t ? `${mod.color}22` : 'transparent',
                    border: `1px solid ${tab === t ? mod.color + '66' : '#1e2d47'}`,
                    color: tab === t ? mod.color : '#475569',
                    borderRadius: '6px', padding: '0.4rem 0.9rem', cursor: 'pointer',
                    fontSize: '0.72rem', fontFamily: "'IBM Plex Mono', monospace", textTransform: 'uppercase', letterSpacing: '0.05em', transition: 'all 0.15s'
                  }}
                >{t}</button>
              ))}
            </div>
          </div>

          {/* Body */}
          <div style={{ flex: 1, overflowY: 'auto', padding: '1.8rem 2rem' }}>

            {showGlossary && (
              <div style={{ marginBottom: '1.5rem', background: '#0d1526', border: '1px solid #1e2d47', borderRadius: '12px', padding: '1.2rem' }}>
                <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 700, color: '#e2e8f0', marginBottom: '1rem', fontSize: '0.9rem' }}>📖 All Key Terms</div>
                <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fill, minmax(280px, 1fr))', gap: '0.6rem' }}>
                  {course.modules.flatMap(m => m.keyTerms).map((t, i) => (
                    <div key={i} style={{ background: '#111d30', borderRadius: '6px', padding: '0.6rem 0.8rem' }}>
                      <div style={{ fontSize: '0.75rem', fontWeight: 600, color: '#e2e8f0', fontFamily: "'Syne', sans-serif", marginBottom: '0.2rem' }}>{t.term}</div>
                      <div style={{ fontSize: '0.7rem', color: '#64748b', lineHeight: 1.5 }}>{t.def}</div>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {tab === 'learn' && (
              <div style={{ maxWidth: '720px' }}>
                <div style={{ background: '#0d1526', border: `1px solid ${mod.color}33`, borderRadius: '12px', padding: '1.8rem', fontSize: '0.88rem' }}>
                  {renderTheory(mod.theory)}
                </div>
                {mod.scenario && (
                  <button onClick={() => setTab('scenario')} style={{ marginTop: '1.2rem', background: `linear-gradient(135deg, ${mod.color}33, ${mod.color}11)`, border: `1px solid ${mod.color}55`, borderRadius: '8px', padding: '0.8rem 1.4rem', color: mod.color, cursor: 'pointer', fontFamily: "'Syne', sans-serif", fontWeight: 600, fontSize: '0.85rem', transition: 'all 0.15s' }}>
                    → Try the Scenario Exercise
                  </button>
                )}
              </div>
            )}

            {tab === 'scenario' && mod.scenario && (
              <div style={{ maxWidth: '720px' }}>
                {/* Scenario header */}
                <div style={{ background: `${mod.color}11`, border: `1px solid ${mod.color}33`, borderRadius: '12px', padding: '1.4rem', marginBottom: '1.2rem' }}>
                  <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 700, color: mod.color, fontSize: '0.85rem', marginBottom: '0.6rem' }}>📋 {mod.scenario.title}</div>
                  <div style={{ fontSize: '0.85rem', lineHeight: 1.7, color: '#94a3b8' }}>{mod.scenario.description}</div>
                </div>

                <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 600, color: '#e2e8f0', fontSize: '0.9rem', marginBottom: '0.8rem' }}>{mod.scenario.question}</div>
                {mod.scenario.multiSelect && <div style={{ fontSize: '0.72rem', color: '#475569', marginBottom: '0.8rem', fontFamily: "'IBM Plex Mono', monospace" }}>SELECT ALL THAT APPLY</div>}

                <div style={{ display: 'flex', flexDirection: 'column', gap: '0.7rem' }}>
                  {mod.scenario.options.map((opt, i) => {
                    const isSelected = selected.includes(i);
                    const showResult = submitted;
                    const isCorrect = opt.correct;
                    let borderColor = '#1e2d47';
                    let bg = '#0d1526';
                    if (isSelected && !showResult) { borderColor = mod.color + '88'; bg = mod.color + '11'; }
                    if (showResult && isCorrect) { borderColor = '#10B981'; bg = '#10B98111'; }
                    if (showResult && isSelected && !isCorrect) { borderColor = '#EF4444'; bg = '#EF444411'; }

                    return (
                      <div key={i}>
                        <button
                          onClick={() => handleSelect(i)}
                          className="option-btn"
                          style={{ width: '100%', textAlign: 'left', background: bg, border: `1px solid ${borderColor}`, borderRadius: '10px', padding: '1rem 1.2rem', cursor: submitted ? 'default' : 'pointer', transition: 'all 0.15s', display: 'flex', alignItems: 'flex-start', gap: '0.8rem' }}
                        >
                          <div style={{ width: '20px', height: '20px', minWidth: '20px', border: `2px solid ${isSelected ? mod.color : '#2a3550'}`, borderRadius: mod.scenario.multiSelect ? '4px' : '50%', background: isSelected ? mod.color + '44' : 'transparent', display: 'flex', alignItems: 'center', justifyContent: 'center', marginTop: '1px', transition: 'all 0.15s' }}>
                            {isSelected && <div style={{ width: '8px', height: '8px', borderRadius: mod.scenario.multiSelect ? '2px' : '50%', background: mod.color }} />}
                          </div>
                          <span style={{ fontSize: '0.85rem', color: '#cbd5e1', lineHeight: 1.6 }}>{opt.text}</span>
                          {showResult && (isCorrect ? <span style={{ marginLeft: 'auto', color: '#10B981', fontSize: '1rem' }}>✓</span> : isSelected ? <span style={{ marginLeft: 'auto', color: '#EF4444', fontSize: '1rem' }}>✗</span> : null)}
                        </button>
                        {showResult && (isSelected || isCorrect) && (
                          <div style={{ background: isCorrect ? '#10B98108' : '#EF444408', border: `1px solid ${isCorrect ? '#10B98133' : '#EF444433'}`, borderTop: 'none', borderRadius: '0 0 10px 10px', padding: '0.8rem 1.2rem 0.8rem 3.4rem', fontSize: '0.8rem', color: isCorrect ? '#6ee7b7' : '#fca5a5', lineHeight: 1.6 }}>
                            {opt.feedback}
                          </div>
                        )}
                      </div>
                    );
                  })}
                </div>

                {!submitted ? (
                  <button onClick={handleSubmit} disabled={selected.length === 0} style={{ marginTop: '1.2rem', background: selected.length > 0 ? `linear-gradient(135deg, ${mod.color}, ${mod.color}99)` : '#1e2d47', border: 'none', borderRadius: '8px', padding: '0.8rem 2rem', color: selected.length > 0 ? '#000' : '#334155', cursor: selected.length > 0 ? 'pointer' : 'not-allowed', fontFamily: "'Syne', sans-serif", fontWeight: 700, fontSize: '0.85rem', transition: 'all 0.2s' }}>
                    Submit Answer
                  </button>
                ) : (
                  <div style={{ marginTop: '1.2rem', display: 'flex', gap: '0.8rem', alignItems: 'center' }}>
                    <div style={{ background: allCorrect ? '#10B98122' : '#F59E0B22', border: `1px solid ${allCorrect ? '#10B98155' : '#F59E0B55'}`, borderRadius: '8px', padding: '0.7rem 1.2rem', color: allCorrect ? '#6ee7b7' : '#fcd34d', fontSize: '0.8rem', fontFamily: "'IBM Plex Mono', monospace" }}>
                      {allCorrect ? '✓ EXCELLENT ANALYSIS' : '◈ REVIEW THE FEEDBACK ABOVE'}
                    </div>
                    {currentModule < course.modules.length - 1 && (
                      <button onClick={nextModule} style={{ background: `linear-gradient(135deg, ${mod.color}, ${mod.color}88)`, border: 'none', borderRadius: '8px', padding: '0.7rem 1.4rem', color: '#000', cursor: 'pointer', fontFamily: "'Syne', sans-serif", fontWeight: 700, fontSize: '0.82rem' }}>
                        Next Module →
                      </button>
                    )}
                    {currentModule === course.modules.length - 1 && (
                      <div style={{ color: '#A855F7', fontSize: '0.85rem', fontFamily: "'Syne', sans-serif", fontWeight: 600 }}>
                        🎓 Course Complete!
                      </div>
                    )}
                  </div>
                )}
              </div>
            )}

            {tab === 'terms' && (
              <div style={{ maxWidth: '720px' }}>
                <div style={{ display: 'grid', gap: '0.8rem' }}>
                  {mod.keyTerms.map((t, i) => (
                    <div key={i} style={{ background: '#0d1526', border: `1px solid ${mod.color}22`, borderRadius: '10px', padding: '1rem 1.2rem', display: 'flex', gap: '1rem', alignItems: 'flex-start' }}>
                      <div style={{ width: '8px', height: '8px', minWidth: '8px', borderRadius: '50%', background: mod.color, marginTop: '0.45rem' }} />
                      <div>
                        <div style={{ fontFamily: "'Syne', sans-serif", fontWeight: 700, color: mod.color, fontSize: '0.85rem', marginBottom: '0.3rem' }}>{t.term}</div>
                        <div style={{ fontSize: '0.83rem', color: '#94a3b8', lineHeight: 1.6 }}>{t.def}</div>
                      </div>
                    </div>
                  ))}
                </div>
                <button onClick={() => { setTab('learn'); }} style={{ marginTop: '1.2rem', background: 'transparent', border: `1px solid ${mod.color}44`, borderRadius: '8px', padding: '0.6rem 1.2rem', color: mod.color, cursor: 'pointer', fontSize: '0.8rem', fontFamily: "'IBM Plex Mono', monospace" }}>
                  ← Back to Theory
                </button>
              </div>
            )}
          </div>
        </div>
      </div>
    </>
  );
}
