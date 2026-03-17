# Graduation Paths

Every prototype that receives investment gets one of four outcomes. No exceptions. No "let's revisit this sometime." No prototypes lingering in limbo for two years while someone insists it's "almost ready."

Every path has closure. No zombie prototypes.

---

## The Four Paths

### 1. GRADUATE

**What it means:** This prototype becomes a real product or capability. It gets funded, staffed, and integrated into the product roadmap or operational infrastructure. It leaves the prototyping track entirely.

**Trigger criteria:**
- Scored 20+ in evaluation AND maintained quality during investment phase
- Technical architecture reviewed and approved by engineering leadership
- Security and data compliance reviewed and cleared
- A product owner or business sponsor has formally agreed to own it going forward
- Clear integration path into existing systems is documented
- Cost of ongoing operation is understood and budgeted

**What happens next:**
1. Prototype team presents final demo to leadership and receiving team
2. Handoff plan created: who builds what, by when, with what resources
3. Code moves from prototype repo to the appropriate product/platform repo
4. The receiving team owns it from this point — the prototype team advises for 2-4 weeks during transition
5. Graduation issue closed with outcome documented
6. Announced internally — the submitter and team get visible credit

**Who is responsible:**
- Organising team facilitates the handoff
- Receiving team (product/engineering) owns the build plan
- Original prototype team supports transition
- Executive sponsor ensures resources are actually allocated (not just promised)

**Example:** A team built a prototype that classifies incoming support tickets by urgency and routes them to the right queue. During the investment phase, they tested it on 6 months of real ticket data, achieving 91% accuracy. The support engineering team agrees to own it. It moves into their service repo with a 3-month plan to deploy to production. The prototype team pairs with support engineering for the first two sprints.

---

### 2. ITERATE

**What it means:** The idea is strong, but the prototype isn't ready. Maybe the technical approach needs rethinking. Maybe the business case needs sharper data. Maybe the scope was too ambitious for one cycle. It goes back into the pool for the next cycle with specific, actionable feedback.

**Trigger criteria:**
- Scored 15-19 in evaluation, showing real promise
- Investment phase revealed specific gaps that are addressable
- The core thesis is still valid — the problem is still worth solving
- The team is willing to continue (this is not a forced march)
- Feedback is concrete enough that the team knows exactly what to improve

**What happens next:**
1. Panel writes a clear iteration brief: what worked, what didn't, what needs to change
2. Prototype stays in the repo, tagged with `iterated` label and cycle reference
3. Team has the option (not obligation) to resubmit in the next cycle
4. Resubmission gets no preferential treatment — it competes on merit like everything else
5. But it also gets no penalty — having iterated once is not a mark against it
6. If a prototype iterates twice without graduating, the panel must explicitly decide: one more round or move to SHELVE

**Who is responsible:**
- Review panel writes the iteration brief (not vague — specific and actionable)
- Organising team tracks iterated submissions across cycles
- Original team decides whether to continue
- Nobody pressures the team either way

**Example:** A team built a meeting action-item extractor. It works well on English transcripts from one conferencing tool, but the org uses three different tools and operates in four languages. The panel says: "Strong concept, validated on one platform. For next cycle: support at least two conferencing tools and demonstrate English + one other language. The NLP approach may need to change for multilingual support — consider X or Y."

---

### 3. SHELVE

**What it means:** This prototype has value, but now is not the right time. Maybe the organization isn't ready. Maybe a dependency doesn't exist yet. Maybe the market shifted. The code is preserved, the learnings are documented, and it can be resurrected when conditions change.

**Trigger criteria:**
- The prototype works, but external factors block graduation
- Strategic priorities shifted away from this domain
- A dependency (platform, data source, partner API) isn't available yet but is expected
- The organization can't absorb this right now — too many other things in flight
- OR: the prototype iterated twice without reaching graduation quality

**What happens next:**
1. Panel documents why it's being shelved and what conditions would trigger revisiting
2. Code stays in the repo, tagged with `shelved` label and a "revisit trigger" note
3. Learnings document written: what was discovered, what technical approaches worked/failed
4. The team is explicitly thanked and their work is acknowledged
5. Organising team reviews shelved prototypes at the start of each cycle — if conditions changed, they proactively reach out to the original team
6. After 4 cycles shelved with no revisit trigger met, it moves to KILL automatically

**Who is responsible:**
- Review panel writes the shelving rationale and revisit triggers
- Organising team reviews shelved items each cycle
- Nobody is expected to maintain shelved code — it's frozen in time

**Example:** A team built a tool that automatically generates compliance reports from code repository metadata. It's technically sound, but the org is migrating compliance frameworks next year. Running the prototype on the current framework would create throwaway work. Shelved with trigger: "Revisit once the new compliance framework is in place (expected Q3)."

---

### 4. KILL

**What it means:** This prototype is done. Not failed — done. The team learned something valuable, and now it's time to move on. Killing a prototype is not a punishment. It's an honest acknowledgment that this particular path doesn't lead somewhere worth going.

**Trigger criteria:**
- Investment phase revealed fundamental flaws in the approach or thesis
- The problem it solves turned out to be smaller than estimated
- A commercial solution emerged that does this better and cheaper
- Technical barriers are insurmountable with current capabilities
- The team lost interest or momentum (this is valid — forced prototyping produces garbage)
- Shelved for 4 cycles with no revisit trigger met

**What happens next:**
1. Panel documents what was learned — this is the most important step
2. Learnings are added to the cycle's retrospective and searchable for future teams
3. Code stays in the repo (never delete), tagged with `killed` label
4. The team is explicitly thanked. Killing early is better than wasting 6 more months.
5. Issue closed with full documentation
6. If the team built reusable components, those are extracted and made available

**Who is responsible:**
- Review panel writes the kill rationale and learnings
- Organising team ensures learnings are captured and findable
- The team has no further obligations

**Example:** A team built a prototype that predicts employee attrition from internal communication patterns. During the investment phase, the legal team flagged that analyzing employee communications for this purpose violates the org's privacy policy and possibly labor regulations. The technical approach works, but it can't be deployed. Killed with learning: "Communication pattern analysis is technically feasible but legally constrained. Future prototypes in this space need legal review before investment, not after."

---

## The Rules

1. **Every invested prototype gets an outcome.** Within 2 weeks of the cycle end date, every prototype must be assigned one of the four paths. No exceptions.

2. **Outcomes are documented, not just announced.** A Slack message saying "we killed it" is not closure. The graduation issue template must be filled out completely.

3. **No path is permanent except GRADUATE and KILL.** Shelved prototypes can come back. Iterated prototypes can be shelved or killed. The only permanent states are "it's a real product now" and "we're done with this."

4. **Two iterations max without panel review.** If a prototype has gone through ITERATE twice, the panel must make an active decision. Autopilot iteration is how zombie prototypes happen.

5. **Respect the team's choice.** If a team doesn't want to iterate, that's fine. Nobody is forced to carry a prototype they've lost belief in. Let it shelve or kill gracefully.

6. **Credit is non-negotiable.** Regardless of outcome, the original team is credited. In graduation announcements, in cycle reports, in the dashboard. People who prototype take a risk. That risk gets acknowledged.

---

## At a Glance

| Path | When | What Happens | Timeline |
|------|------|-------------|----------|
| **GRADUATE** | It's ready and the org can absorb it | Funded, staffed, handed off to a product team | Handoff within 4 weeks of decision |
| **ITERATE** | Good idea, not ready yet | Specific feedback given, resubmit next cycle | Team decides within 2 weeks if they'll continue |
| **SHELVE** | Right idea, wrong time | Frozen, documented, reviewed each cycle | Auto-kills after 4 cycles if no trigger met |
| **KILL** | We learned enough | Learnings captured, team thanked, move on | Closed within 1 week of decision |
