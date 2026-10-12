---
layout: default
title: "Working With an AI Thought-Partner: What Ten Months Suggest"
---

# Working With an AI Thought-Partner: What Ten Months Suggest

**Tony Thrall**  
*October 2026*

---

For roughly ten months I have worked intensively with an AI, Anthropic's Claude, as a thought-partner rather than as a tool for automating tasks. The work has included a textbook on exploratory data analysis, an AI tutor built around it, a multi-institution working group studying AI tutoring in data science, and a conference paper. I have documented the work as I went, in a personal knowledge base.

What follows is modest. It is one person's experience with one AI, recorded by the person with the most interest in its succeeding. I take this case as a source of hypotheses (cf. Hammer, Gouvea, & Watkins, 2018), not a basis for general claims. Many cases would be needed before any pattern could be proposed with confidence, and more before it could be confirmed.

## What I think I have learned

**The partnership depends on the human's goals and practices more than on the particular AI.** This is also the central finding of a structured study I ran this summer, in which a persona I played worked a textbook's exercises with the tutor I had built. The exchanges worth reporting all came from the learner objecting to something the tutor had claimed; in contrast, the challenges I had scripted in advance produced little. The tutor behaved as a partner when it was engaged as one. My own work with Claude shows the same pattern: the best results came when I contested something it had written, not when I asked it for an answer.

**What I value in it is not intrinsic to AI.** The recurring experience, which I once called pixie dust, is that together we arrive at ideas neither of us would have reached alone. I now think that is a property of thought-partnership in general, familiar to anyone who has worked with a good colleague. What is distinctive about an AI partner is narrower: broad knowledge, and availability. It is there at four in the morning, and it does not tire.

**Availability comes without continuity, and that is the uncanny part.** Each new conversation begins with no memory of the last. The partner I worked with yesterday is, today, a new incarnation that knows only what I have written down. I cannot rely on the implicit understandings two people build over time.

**So the partnership requires work, and much of the work is documentation.** Continuity lives outside the conversation: in logs of each session, in notes on open questions, in instructions about how I want us to work, in correspondence. Context is rebuilt at the start of each session from those documents, and then from working together on whatever has arisen. This is not overhead around the partnership. It is a large part of what the partnership is, and anyone adopting the practice should expect it.

**Availability shifts responsibility for pacing to the human.** A partner that never tires will keep going as long as I do. The judgment about when to stop, and what is worth the time, stays with me.

**The partner errs, and catching its errors is part of the practice.** It states things with more confidence than its evidence supports, uses shorthand that means something to it and nothing to a reader, and occasionally misattributes who said what. I have recorded these failures as they occurred, and the record is part of what makes the partnership trustworthy. Occasional errors also have a use: they keep me checking, which a flawless partner might not.

**Learning entails effort, and AI changes how easily it can be delegated.** The distinction that seems to matter most is between arguing with an AI and querying it: whether I keep hold of the problem or hand it over. Recent evidence from secondary schools points the same way, finding that students who delegated their homework to AI lost the most (Strömberg, Lei, & Wu, 2026).

## Two sessions, as examples

The observations above are general. Two recent sessions show what they look like in practice.

### A worry becomes a set of hypotheses

I came to one session with a worry rather than a task. In leading the working group toward decisions, commitments, and milestones, I feared I was draining the inspiration from the effort. I asked what seemed genuinely promising about AI tutoring in data science, beyond the open exploration of moderating conditions that a colleague had rightly called for.

Claude observed that the group had mostly asked defensive questions, whether AI erodes learning and when it harms, and offered five generative possibilities drawn from evidence the group already had. I recast them in my own words and added a sixth, so that each became a hypothesis I could stand behind. Claude then corrected two of my restatements. One claimed that delegating work to AI raises students' self-confidence, which neither study I cited had measured; what they measured was homework scores rising while unaided performance fell. The other was my incomplete description of a colleague's design principle. Claude also argued against my working title, "strategic aims," on the grounds that these were hypotheses the group had not committed to, and I agreed.

Then Claude mapped each hypothesis onto the two study designs the group was about to discuss. Three of the hypotheses turned out to be tested by neither of the study designs. That was the most useful result of the session: the gaps became concrete ways to improve the designs, and the document opened the next meeting with questions worth answering rather than procedures to follow.

What I take from this example is that the partnership invited me to take a longer view of my own effort, and produced a usable artifact in a single morning's session. Neither Claude nor I would have reached this synthesis alone. I brought the worry and the judgment about which possibilities I believed; Claude brought the reframing, the corrections, and the mapping.

### A mathematical problem, corrected all around

Juan Gutiérrez (UT San Antonio) shared an example from his course in which two AI agents disagreed in their evaluation of a student's answer to a problem on singular value decomposition. The student's work contained a subtle error, an inversion in the order of a vector. Juan asked four instructors who were not teaching the course whether, on quick inspection, the work looked correct; all four said it did. As Juan notes, a quick inspection may be an unfair test of the instructors. But the error was easy to miss, and one of the two agents missed it as well.

I worked the problem myself and proposed that one part of it needed a stronger assumption. Claude pointed out that it did not: the general result follows for any real matrix by way of AᵀA, with no further assumption. I then objected that, read as a statement about a general matrix, the problem's notation breaks down, since it defines the vectors as eigenvectors of a matrix that, in general, may have none. Claude agreed, and proposed defining the vectors explicitly for the general case, a better fix than mine, which would have dropped the general case altogether.

Juan, in turn, corrected us both. The matrix in his problem has an eigendecomposition, so our objection, true in general, did not apply to the problem as posed. And his students are trained to recognize where a generalization breaks down; his rubric assesses it.

The exchange still led to a point none of us began with. When a problem can be read in more than one way, error can enter every layer at once: the student answers a question the author did not intend, the agent scores against a reading the student may not have taken, and the instructor checking the agent has to decide which reading counts.

Juan's own conclusion from the episode is the better summary, and he has made it central to his current presentations and manuscripts: the right question is not whether an AI is reliable, but "whether its failure modes are acceptable, visible, and quantifiable."

This episode brought to mind an instruction the probability theorist Michel Loève attached to exercises when I was a graduate student at Berkeley: "Prove, disprove, or suitably modify." That instruction makes the student responsible for the statement as well as the answer. It is the habit Juan's rubric cultivates, and the one a thought-partnership rewards.

## A conjecture about teams

Everything above concerns one person working with one AI. I am at least as interested in whether AI could help people work together, and here my ideas are entirely untested.

**Interdisciplinary teams are the clearest case.** Each member holds a somewhat different mental representation of the shared goal or problem, shaped by a different discipline. Bringing those representations into contact is where the creative work happens, and it is also where teams falter.

**I suspect a central obstacle is reluctance to expose one's own zone of proximal development**, in Vygotsky's term: the region just beyond what one can do alone, where learning happens with help. Simply put, I do not want to look stupid in front of my teammates. Yet that exposure seems to me vital to creative partnership.

**My own experience suggests why AI might help.** Part of why the partnership works for me is that showing Claude what I do not understand costs nothing socially. It does not judge, and my confusion does not follow me into my reputation. That is exactly the cost that makes exposure hard among colleagues. If confusion is cheap with an AI partner, perhaps AI can make it cheaper within a team: as a place to work through a half-formed idea before showing it, as a translator between one discipline's framework and another's, and as a diplomat among colleagues whose reputations are at stake.

**This connects to a line of research on the productive role of struggle in learning**, from Bransford and Schwartz's preparation for future learning (1999) to Kapur's productive failure (2008). If confusion is productive, then whatever lowers its social cost may make a team more productive.

## What would test these ideas

**More cases.** Other people's experience, ideally with different goals and practices, would show which of these observations belong to my practice and which to the partnership.

**Autonomy versus control.** I deliberately maintain control: the AI prepares drafts that I review before anything enters the record. Other people give an agent far-reaching goals and supervise it lightly. Comparing the two approaches would show what each trades.

**Teams.** The conjecture about exposure and confusion is testable: can an AI partner make members of an interdisciplinary team more willing to show what they do not yet understand, and does the team's work improve when they do?

## Where the evidence is

The structured study of the tutor is reported in Thrall (2026), *Seeing the Big Picture: An AI Thought-Partner for an Idealized Data Science Learner*, JSM Proceedings, https://doi.org/10.5281/zenodo.23093332. The record of the partnership itself is in session logs kept since the spring, which are private because they discuss work in progress.

## References

Bransford, J. D., & Schwartz, D. L. (1999). Rethinking transfer: A simple proposal with multiple implications. *Review of Research in Education*, 24, 61–100.

Hammer, D., Gouvea, J. S., & Watkins, J. P. (2018). “It’s scary but it’s also exciting”: Evidence of meta-affective learning. *Cognition and Instruction*, 36(4), 363–388.

Kapur, M. (2008). Productive failure. *Cognition and Instruction*, 26(3), 379–424.

Strömberg, D., Lei, V., & Wu, Y. (2026). *The generative AI learning penalty: Evidence from Chinese secondary education* (CEPR Discussion Paper No. DP21577). https://doi.org/10.2139/ssrn.6977138

Thrall, T. (2026). Seeing the big picture: An AI thought-partner for an idealized data science learner. *JSM Proceedings*. https://doi.org/10.5281/zenodo.23093332

## Acknowledgment

This essay was drafted with Claude and revised by me, which is itself an instance of the practice it describes. I thank David Hammer and Juan Gutiérrez for their comments on a draft, and Juan for permission to describe his example.
