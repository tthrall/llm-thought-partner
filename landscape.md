---
layout: default
title: "LLM-Enhanced Learning: A Thought-Partner Alternative"
---

# LLM-Enhanced Learning: A Thought-Partner Alternative

**Tony Thrall**  
*February 2026*

---

**Abstract.** The emergence of LLM-based learning tools presents both opportunities and risks for data science education. Most current tools default to answer-provision, which risks undermining the deep understanding that employers increasingly demand. This paper surveys the landscape, diagnoses the structural incentives behind the answer-provider problem, and proposes a "thought-partner" alternative grounded in five pedagogical principles. An instantiation of this approach—the EDA Companion—is currently in alpha testing.

<br>

## Introduction

In the fall of 2022, OpenAI released ChatGPT, accelerating a race to develop and deploy large language models across virtually every domain. Education has been no exception. Within months, institutions faced urgent questions about academic integrity, while entrepreneurs rushed to build LLM-powered tutoring systems, coding assistants, and learning companions.

These developments arrive in the context of a decades-old endeavor. Computer-assisted instruction traces back through intelligent tutoring systems of the 1970s and 80s, programmed instruction of the 1960s, and teaching machines even earlier (see Zhang & Li, 2024; Suppes & Sheehan, 1988). This paper does not attempt to survey that history comprehensively. Rather, it situates the current generation of LLM-based tools within ongoing debates about how technology can support—or undermine—genuine learning.

The central argument is this: most current LLM-based learning tools default to answer-provision, which feels helpful but risks creating dependency and the illusion of competence. An alternative approach—treating the LLM as a thought-partner rather than an answer-provider—may better serve learners' long-term interests. This paper surveys the landscape, diagnoses the answer-provider problem, proposes a thought-partner alternative grounded in five pedagogical principles, and describes an early instantiation of the approach.

## The Learning Agent Landscape

The current landscape of LLM-based learning tools can be organized into four broad categories, each with distinct strengths and limitations.

**K-12 tutoring agents** represent the most pedagogically sophisticated applications. Khan Academy's Khanmigo, for example, employs Socratic prompting and hint progressions rather than simply providing answers (Khan Academy, 2024). These tools typically include teacher dashboards for progress monitoring and are designed for guided discovery with adaptive pacing. Their limitation for our purposes is that they assume younger learners; the scaffolding that serves a middle schooler may feel excessive or patronizing to an adult professional.

**Professional skills training** tools focus on soft skills development through conversation simulation and role-play. Products like Skillsoft's CAISY enable practice of interpersonal scenarios with AI-generated feedback. While valuable for leadership development or customer service training, these tools rarely address technical or conceptual mastery—the domains where data science learners most need support.

**Coding assistants** present the answer-provider problem in its starkest form. GitHub Copilot and similar tools are optimized for productivity: they complete code, generate functions, and solve problems on the developer's behalf. This is precisely what professional developers want when shipping software. But for learners, the cost is significant. A student who uses Copilot to complete every assignment may never develop the capacity to debug independently. Harvard's CS50 Duck represents an interesting counterpoint—a debugging assistant designed with Socratic elements (Harvard University, 2024)—though even it must contend with students who simply want the answer.

**General-purpose LLMs** like ChatGPT, Claude, and Gemini are powerful but pedagogically neutral. They can function as either answer-providers or thought-partners, depending entirely on how the interaction is structured. In principle, a disciplined learner could prompt these tools to ask questions rather than provide answers. In practice, most users take the path of least resistance, and the tools are optimized to feel helpful in ways that map to answer-provision.

What emerges from this survey is a gap. K-12 tools are designed for children. Professional training tools focus on soft skills. Coding assistants prioritize efficiency over understanding. General LLMs require the learner to impose pedagogical discipline that most won't maintain. The underserved population is adult learners in technical domains who need conceptual depth—precisely the population entering or advancing in data science careers.

## The Answer-Provider Problem

Why do learning tools default to providing answers? The explanation lies in structural incentives rather than poor intentions.

User satisfaction metrics reward speed and perceived helpfulness. When a learner asks a question and receives a clear, immediate answer, they feel helped. When they receive a question in return, they may feel frustrated. Product teams measuring engagement and satisfaction will naturally optimize for the former.

The evaluation problem compounds this. "Correct answer delivered" is straightforward to measure. "Productive struggle supported" is not. In the absence of good metrics for genuine learning, proxies like task completion and user satisfaction become the de facto goals.

Commercial pressure reinforces these dynamics. Users want to feel helped, not challenged. A tutoring product that consistently withholds answers—even in service of deeper understanding—risks losing users to competitors who provide what users think they need.

Finally, LLM training itself optimizes for helpfulness, which the models (and their developers) naturally interpret as providing what the user requests. When a user asks "what's the answer?", the helpful response appears to be providing the answer.

### Consequences for Learning

The learning sciences have long established that genuine understanding requires active construction, not passive reception (Dewey, 1916; Piaget, 1954). Information received without cognitive effort is forgotten faster than information the learner worked to construct. Bjork and Bjork (2011) describe this as the principle of "desirable difficulties"—conditions that make learning harder in the short term but more durable in the long term. When tools provide answers on demand, several problematic patterns emerge.

Retention suffers because the learner has not done the cognitive work of organizing and integrating the information. Dependency forms as learners come to outsource thinking rather than develop their own capabilities. Perhaps most insidiously, an illusion of competence develops: getting the right answer feels like understanding, even when the learner could not reproduce the reasoning independently. Over time, metacognitive skills—the capacity to monitor one's own understanding and direct one's own learning—may atrophy from disuse.

Kapur (2008) has shown that students who struggle with problems before receiving instruction often learn more deeply than those who receive instruction first—a phenomenon he terms "productive failure." The answer-provider model inverts this sequence, providing solutions before students have had the opportunity to struggle productively.

### The Design Tension

The fundamental tension is this: LLMs are capable of providing answers instantly, and users want answers instantly. Any pedagogical approach must work against both the tool's default behavior and the user's immediate preferences, in service of the user's long-term interests.

This is not a new tension—it is the ancient challenge of education itself. What is new is the availability of infinitely patient tools that can provide unlimited answers without judgment. The question is whether these same tools can be designed to support deeper understanding instead.

## The Thought-Partner Alternative

What if LLM interactions were designed around a different goal: not to provide answers, but to deepen the learner's own thinking? This requires explicit pedagogical commitments embedded in system design and reinforced through interaction patterns.

The thought-partner approach draws on constructivist theories of learning associated with Dewey (1916) and Piaget (1954), which hold that understanding is actively built by the learner rather than passively received. It also draws on Vygotsky's (1978) insight that thinking originates in social dialogue and that articulation is constitutive of understanding—we clarify our thoughts by expressing them to others. And it reflects Greeno's (1998) perspective that cognition is situated across people, tools, and environments rather than contained solely in individual minds.

These theoretical foundations suggest that an AI which asks questions and elicits explanation may support deeper understanding than one which provides answers, because the cognitive work of construction and articulation is where learning happens.

### Five Foundational Principles

The thought-partner approach can be operationalized through five principles.

**Human Accountability.** The learner remains responsible for all conclusions and decisions. The thought-partner asks questions, surfaces considerations, and identifies gaps—but the learner synthesizes and decides. If asked "what's the answer?", the thought-partner redirects to "what's your current thinking?"

**Student as Teacher.** The learner demonstrates understanding by explaining concepts to the thought-partner, which probes for clarity, coherence, and completeness. Explaining forces organization of thought; gaps become visible through the act of articulation. This principle draws on research showing that generative activities—explaining, elaborating, self-questioning—produce deeper understanding than passive reception (Chi & Wylie, 2014).

**Deliberate Skepticism.** The thought-partner questions assumptions, asks for evidence, and avoids premature validation. Rather than "that's right!", it asks "how do you know?" or "what would change your mind?" This builds habits of intellectual rigor and models the internal dialogue of expert practitioners.

**Facilitated Autonomy.** The thought-partner provides minimal scaffolding necessary for progress, then withdraws. Hints before answers; questions before hints; patience before questions. Struggle is where learning happens; premature rescue short-circuits the process (Kapur, 2014).

**Transparent Process.** The thought-partner makes its pedagogical approach visible and invites reflection on the learning process itself. Metacognitive awareness supports transfer to contexts without thought-partner support.

### How This Differs

| Dimension        | Typical Learning Agent | Thought-Partner            |
| ---------------- | ---------------------- | -------------------------- |
| Default response | Provide answer         | Ask clarifying question    |
| Success metric   | Task completion        | Demonstrated understanding |
| Scaffolding      | Maximize support       | Minimize support           |
| Learner role     | Recipient              | Active constructor         |
| Pedagogy         | Hidden                 | Explicit                   |

The distinction between Socratic tutoring and thought-partnership deserves emphasis. Socratic tutoring is a technique—a method of leading learners toward predetermined answers through carefully sequenced questions. Intelligent tutoring systems have long employed such techniques (Graesser et al., 2004; VanLehn, 2011). Thought-partnership is a relationship—an ongoing collaboration in which the AI supports the learner's thinking without directing it toward specific conclusions. The tutor knows the answer and guides the student toward it. The thought-partner helps the student develop their own answer and subjects it to scrutiny.

## An Instantiation: The EDA Companion

The EDA Companion is a pedagogical agent designed for students working through *Exploratory Data Analysis for Machine Learning* (Thrall, 2026a), a Master's-level textbook bridging *R for Data Science* (Wickham, Çetinkaya-Rundel, & Grolemund, 2023) and *Introduction to Statistical Learning* (James, Witten, Hastie, Tibshirani, & Taylor, 2023). The target audience—aspiring data scientists with varying preparation—exemplifies the underserved population identified earlier: adult learners in technical domains who need conceptual depth.

The five principles are embedded in the Companion's system prompt as behavioral constraints. The Companion is currently in alpha testing with two subjects, with data collection via post-session surveys and conversation logs. A demonstration transcript is available at [tthrall.github.io/llm-thought-partner](https://tthrall.github.io/llm-thought-partner/) (Thrall, 2026b).

This is early-stage work. The Companion represents a proof of concept, not a validated intervention.

## Implications

<strong>Educators.</strong> The thought-partner framing offers a path beyond the "ban or allow" debate that has dominated institutional responses to LLMs. The question becomes not whether students use AI tools, but how those interactions are structured. Companion-style tools might supplement office hours and peer collaboration, extending the reach of human instruction without replacing it.

<strong>Curriculum design.</strong> The implications are significant. Assignments may need redesign to be compatible with thought-partner interaction—emphasizing process documentation and reasoning, not just final products. Learning objectives should specify the understanding students should demonstrate, not just the outputs they should produce. Assessment must evolve to evaluate whether students can reason independently, not just whether they can produce correct answers.

<strong>Workforce development.</strong> A central concern of this year's ADSA Leadership Summit, the thought-partner approach addresses a pressing challenge. Entry-level hiring is declining as routine tasks shift to AI. Graduates must demonstrate value beyond what AI provides. Tools that build genuine capability, rather than dependency, serve both learners and employers.

## Directions for Development

The thought-partner approach raises questions that can only be answered through sustained development and study. How do learners respond to deliberate non-answering over multiple sessions—does productive frustration give way to unproductive frustration? Where is the boundary between scaffolding that enables progress and scaffolding that undermines autonomy? How do these principles translate across domains, from conceptual learning to debugging to creative work?

Beyond these research questions lie design challenges. How should a thought-partner retain knowledge across sessions—of content scope, learner preferences, and demonstrated progress? How might records of learning conversations be shared with learners themselves, supporting metacognitive reflection and communication with instructors or employers?

These are not questions a single researcher can answer. They require collaboration across learning scientists, educators, technologists, and—crucially—learners themselves. The EDA Companion is one attempt to instantiate the thought-partner approach. Others will be needed.

For those interested in engaging with this work, a demonstration transcript and the alpha-testing survey instrument are available at [tthrall.github.io/llm-thought-partner](https://tthrall.github.io/llm-thought-partner/). The author welcomes correspondence at tthrall@alumni.stanford.edu.

## References

Bjork, E. L., & Bjork, R. A. (2011). Making things hard on yourself, but in a good way: Creating desirable difficulties to enhance learning. In M. A. Gernsbacher, R. W. Pew, L. M. Hough, & J. R. Pomerantz (Eds.), *Psychology and the real world: Essays illustrating fundamental contributions to society* (pp. 56–64). Worth Publishers.

Chi, M. T. H., & Wylie, R. (2014). The ICAP framework: Linking cognitive engagement to active learning outcomes. *Educational Psychologist*, *49*(4), 219–243. https://doi.org/10.1080/00461520.2014.965823

Dewey, J. (1916). *Democracy and education*. Macmillan.

Graesser, A. C., Lu, S., Jackson, G. T., Mitchell, H. H., Ventura, M., Olney, A., & Louwerse, M. M. (2004). AutoTutor: A tutor with dialogue in natural language. *Behavior Research Methods, Instruments, & Computers*, *36*(2), 180–192. https://doi.org/10.3758/BF03195563

Greeno, J. G. (1998). The situativity of knowing, learning, and research. *American Psychologist*, *53*(1), 5–26. https://doi.org/10.1037/0003-066X.53.1.5

Harvard University. (2024). *CS50 Duck Debugger*. https://cs50.ai/

James, G., Witten, D., Hastie, T., Tibshirani, R., & Taylor, J. (2023). *An introduction to statistical learning with applications in Python*. Springer. https://www.statlearning.com/

Kapur, M. (2008). Productive failure. *Cognition and Instruction*, *26*(3), 379–424. https://doi.org/10.1080/07370000802212669

Kapur, M. (2014). Productive failure in learning math. *Cognitive Science*, *38*(5), 1008–1022. https://doi.org/10.1111/cogs.12107

Khan Academy. (2024). *Khanmigo: AI for education*. https://www.khanacademy.org/khan-labs

Piaget, J. (1954). *The construction of reality in the child*. Basic Books. (Original work published 1937)

Suppes, P., & Sheehan, J. (1988). *The development of CAI: An expert system in education* (Technical Report). Stanford University, Institute for Mathematical Studies in the Social Sciences. https://files.eric.ed.gov/fulltext/ED304483.pdf

Thrall, T. (2026a). *Exploratory data analysis for machine learning*. https://tthrall.github.io/eda4ml/

Thrall, T. (2026b). *LLM as thought-partner: A demonstration of Socratic AI tutoring*. https://tthrall.github.io/llm-thought-partner/

VanLehn, K. (2011). The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems. *Educational Psychologist*, *46*(4), 197–221. https://doi.org/10.1080/00461520.2011.611369

Vygotsky, L. S. (1978). *Mind in society: The development of higher psychological processes* (M. Cole, V. John-Steiner, S. Scribner, & E. Souberman, Eds.). Harvard University Press.

Wickham, H., Çetinkaya-Rundel, M., & Grolemund, G. (2023). *R for data science: Import, tidy, transform, visualize, and model data* (2nd ed.). O'Reilly Media. https://r4ds.hadley.nz/

Zhang, Y., & Li, W. (2024). The development history and future trend of computer-assisted teaching. *Journal of Education and Educational Research*, *7*(1), 215–219. https://doi.org/10.54097/jeer.v7i1.14

---

*Tony Thrall is a former NSA data scientist and co-chair of the ADSA Leadership Summit panel on Student Readiness and Workforce Development in this Era of AI. He is completing a textbook on exploratory data analysis for machine learning.*
