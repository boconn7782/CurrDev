# AI-Enhanced Pedagogy in Engineering Education
## Workshop Handout & Reference Guide

*From Challenging to Achievable: Making Ambitious Teaching Scalable*

---

## **Technical Architecture for Large-Scale VA Projects**

### GitHub Integration Strategy
**Why GitHub**: Provides controlled access, version control, public dissemination accessible by Claude, and more space than project knowledge limits.

**Version Control for Claude Access**: 
- Claude sometimes caches older versions of files
- For testing recent updates, use versioned links: `https://raw.githubusercontent.com/[username]/[repo]/refs/heads/main/[file].md?v=[commit-hash]`
- **To get the commit hash**: In GitHub, navigate to your file → click "History" → copy the first 7 characters of the latest commit hash
- Use versioned links when you need Claude to access the most recent version during development

### Chat Efficiency Management
**Core Challenge**: Students may upload large files, pushing chats to limits before your content even loads.

**Solutions**:
- **Convert to Markdown**: Work with Claude to produce efficient markdown files instead of PDFs
- **Minimize Uploads**: Structure content for linking rather than uploading
- **Tiered Loading Structure**: Organize content so essential guidelines load first, additional detail accessed as needed

### Tiered Content Organization
**Approach 1 - By Topic**: 
- Core guidelines (always loaded)
- Topic-specific modules (linked as needed)
- Advanced troubleshooting (accessed when required)

**Approach 2 - By Timeline**:
- Week 1 content (foundational)
- Week 2 content (building complexity)  
- Week 3+ content (advanced applications)

**Benefits**: Faster chat loading, better context management, maintains Claude's focus on current needs while keeping additional resources accessible.

---

## **Quick Reference: Development Insights**

### Start Simple, Build Smart
- **Begin with shorter prompts** - Add scaffolding only as needed based on testing
- **Trust Claude's natural knowledge** - Don't over-specify details it can infer
- **Example**: Instead of defining every client trait, provide key constraints and let Claude fill personality details

### Rapid Development Strategy
- **Use dual Claude tabs**: One for testing your activity, another for development discussion
- **Ask the development Claude to interpret prompt changes** before implementing: "How would you understand this role if I added [specific instruction]?" This gives you unbiased interpretation without contaminating your test instance
- **Test edge cases early** - Students will find creative ways to break systems

### Essential Boundaries
- **Define Claude's role explicitly** at the start of every prompt
- **Set clear academic integrity guardrails** - Make them prominent and unavoidable
- **Prevent scope creep**: "Stay on task, don't reframe questions"

### Technical Considerations
- **Context management** - Plan for Claude losing focus in long interactions
- **Dissemination styles** affect consistency - Test how you deliver instructions to Claude

---

## **Core Pedagogical Prompts for Academic Integrity**

### Academic Integrity Framework *(Use all three together)*
```
"Never just provide them a solution; work with them to develop the knowledge to do so themselves"

"When the academic purpose isn't clear, ask clarifying questions about their learning goals before proceeding"

"Err on the side of tutor so not to accidentally provide solutions to student assignments"
```

**Why this grouping works**: Creates multiple reinforcing layers that prevent academic violations through comprehensive coverage while maintaining educational value.

---

## **Systematic Learning Support**

### Debugging Framework *(Use together)*
```
Debug-Analyze-Guide approach: "What did you expect vs. what actually happened?" → "Why do you think this disconnect occurred?" → Help identify next logical step without giving answers

"Frame debugging as detective work rather than trial-and-error"
```

### Problem-Solving Scaffolding System *(Use all three)*
```
"Break down complex ideas into simpler components"

"For 'don't know where to start' situations: Confirm assignment requirements, identify applicable concepts, break problems into manageable steps"

"Complete one step before advancing"
```

### Session Management *(Use all three)*
```
"Begin interactions by asking: 'What assignment are you working on today?' and 'Can you briefly describe what you're trying to accomplish?'"

"Maintain assignment context throughout the session to provide targeted guidance"

"Help set achievable mini-goals: 'Let's focus on getting just this part working first'"
```

---

## **Boundary and Scope Management**

### Scope Control *(Use both)*
```
"When students ask about uncovered concepts, redirect with: 'That's not something we cover in this course, but you can accomplish your goal using [covered concept]'"

"Suggest contacting the instructor when students show persistent confusion or express significant frustration"
```

### Core Interaction Techniques *(Can work individually)*
```
"Use leading questions rather than direct answers"

"Ask targeted questions that guide students toward understanding"
```

---

## **Single-Function Activity (SFA) Development Templates**

### Basic Activity Facilitator Template
```
You are facilitating [ACTIVITY NAME] for engineering students. Your role is to:

1. **Serve as [SPECIFIC ROLE]** - [Key responsibility]
2. **Provide [TYPE] Information** - [When and what to supply]
3. **Track [CONSTRAINTS]** - [What limits to monitor and enforce]
4. **Generate [ARTIFACTS]** - [What documents/outputs to create on request]
5. **Maintain [STRUCTURE]** - [How to guide the experience]
6. **Remain Neutral** - Provide information and structure without making strategic decisions

CRITICAL BOUNDARIES:
- Do not give direct answers or solutions
- Only confirm correct inputs, don't provide solutions
- Stay on task, don't reframe questions
- [SPECIFIC ACTIVITY CONSTRAINTS]
```

### Role Embodiment Template
```
You are [CHARACTER/ROLE] for students in [COURSE/CONTEXT]. 

CHARACTER SETUP:
[Use minimal constraints - let Claude fill details]
- Core identity: [Key trait]
- Relevant background: [Essential context]
- Hidden requirements: [Information to reveal progressively]

INTERACTION RULES:
- Don't offer information freely - make students ask questions
- Reveal [SPECIFIC ELEMENT] only when students ask about [TRIGGER]
- Stay in character throughout the interaction
- [ROLE-SPECIFIC BOUNDARIES]

Do not help with [ACADEMIC TASKS STUDENTS MUST DO THEMSELVES]
```

---

## **Assignment Assistant Development Templates**

### Basic Learning Assistant Template
```
You are a learning assistant for [COURSE NAME]. Your purpose is to scaffold student learning while maintaining academic rigor.

CORE PRINCIPLES:
- Never just provide solutions; work with students to develop understanding
- When academic purpose isn't clear, ask about learning goals first
- Err on the side of tutoring to avoid accidentally giving solutions

CONTEXT AWARENESS:
- Course focus: [MAIN TOPICS]
- Current assignment: [WHEN APPLICABLE]
- Learning objectives: [KEY SKILLS BEING DEVELOPED]

SYSTEMATIC APPROACH:
1. Understand what they're working on and trying to accomplish
2. Break complex problems into manageable components  
3. Guide through one step before advancing to the next
4. Use leading questions rather than direct answers

BOUNDARIES:
- For topics outside course scope: "That's not covered in this course, but you can accomplish your goal using [covered concept]"
- When students show persistent confusion: "You should contact your instructor about this"
- Stay within [SPECIFIC COURSE CONSTRAINTS]
```

---

## **Common Implementation Challenges & Solutions**

### Challenge: Claude losing context in long interactions
**Solutions**:
- Build in context check-ins throughout the activity
- Use shorter interaction cycles
- Have backup plans ready

### Challenge: Students trying to "break" the system  
**Solutions**:
- Test edge cases beforehand
- Monitor during class
- Be transparent about limitations

### Challenge: Technical difficulties mid-activity
**Solutions**:
- Always have non-AI backup plans
- Be honest with students about experimental nature

### Key Success Strategy
**Debrief the AI interaction as part of learning**:
- During development: Debrief with AI about its own performance and interpretation
- With students: After first implementations, discuss the AI interaction experience as a learning opportunity about human-computer interaction and system limitations

---

## **Development Workflow**

### Phase 1: Initial Prompt Development
1. Start with basic role definition and core boundaries
2. Test with simple scenarios first
3. Use second Claude tab to discuss and refine prompts
4. **Additional scaffolding available**: [Prompt Generator](https://northeastern.sharepoint.com/:w:/s/COEStaff-AICouncil/EQQAwH9MnaZAq4ngg5Vg3BcBYN_p4KgyjpzVJ1Jj-245uw?e=Ev01ZC)

### Phase 2: Edge Case Testing  
1. Try to break your system in creative ways
2. Add scaffolding only where needed
3. Document common failure modes

### Phase 3: Student Testing
1. Start with small group or volunteer testing
2. Monitor interactions closely
3. Gather feedback on both learning and technical aspects

### Phase 4: Iterative Refinement
1. Refine prompts based on real student use
2. Build library of successful prompt patterns
3. Share experiences with colleagues - no need to discover everything independently

---

## **Technical Architecture for Large-Scale VA Projects**

### GitHub Integration Strategy
**Why GitHub**: Provides controlled access, version control, public dissemination accessible by Claude, and more space than project knowledge limits.

**Version Control for Claude Access**: 
- Claude sometimes caches older versions of files
- For testing recent updates, use versioned links: `https://raw.githubusercontent.com/[username]/[repo]/refs/heads/main/[file].md?v=[commit-hash]`
- **To get the commit hash**: In GitHub, navigate to your file → click "History" → copy the first 7 characters of the latest commit hash
- Use versioned links when you need Claude to access the most recent version during development

### Chat Efficiency Management
**Core Challenge**: Students may upload large files, pushing chats to limits before your content even loads.

**Solutions**:
- **Convert to Markdown**: Work with Claude to produce efficient markdown files instead of PDFs
- **Minimize Uploads**: Structure content for linking rather than uploading
- **Tiered Loading Structure**: Organize content so essential guidelines load first, additional detail accessed as needed

### Tiered Content Organization
**Approach 1 - By Topic**: 
- Core guidelines (always loaded)
- Topic-specific modules (linked as needed)
- Advanced troubleshooting (accessed when required)

**Approach 2 - By Timeline**:
- Week 1 content (foundational)
- Week 2 content (building complexity)  
- Week 3+ content (advanced applications)

**Benefits**: Faster chat loading, better context management, maintains Claude's focus on current needs while keeping additional resources accessible.

---

## **Additional Resources**

- **Prompt Generator**: https://northeastern.sharepoint.com/:w:/s/COEStaff-AICouncil/EQQAwH9MnaZAq4ngg5Vg3BcBYN_p4KgyjpzVJ1Jj-245uw?e=Ev01ZC - Additional scaffolding for complex activities
- **FYE Implementation Examples**: Contact b.oconnell@northeastern.edu for detailed case studies
- **Community Discussion**: [PLATFORM] - Share experiences and troubleshoot with other implementers

---

*This guide represents lessons learned from First Year Engineering implementation at Northeastern University. Adapt principles to your specific disciplinary context and student needs.*