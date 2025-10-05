## ImpulsAI — your intelligent assistant to optimize resumes and land jobs

### The Problem

---

Candidates often miss valuable opportunities because their resumes are not optimized for a specific job. Initial screening — performed by both human recruiters and automated systems (ATS — Applicant Tracking Systems) — can discard resumes for lacking the right keywords, having poor formatting, or omitting relevant information.

### The Solution

---

ImpulsAI democratizes access to advanced AI tools, removing the need for users to have prior knowledge of *prompt engineering* or LLMs (Large Language Models) to optimize their documents. The value of our solution lies in leveling the playing field, ensuring a candidate’s potential is fairly evaluated and not prematurely discarded due to an outdated or non-targeted resume.

> ImpulsAI is a Software-as-a-Service (SaaS) platform that uses an intelligent agent engine to analyze the job description and the user’s resume. The tool is more than a simple text generator — it delivers a complete candidate-preparation solution.

The platform provides a package of structured outputs, which include:

* **Smart Resume Customization:** Precise suggestions for keywords, skills and content adjustments to optimize the resume for the target job.
* **Interview Preparation Guide:** A script of interview questions and model answers for both cultural fit and technical interviews, based on the position requirements.
* **Learning Roadmaps:** Suggested courses and study paths to help the candidate fill knowledge gaps and prepare technically for the role.

### Challenges Faced

---

During the project development the team encountered significant technical and business challenges. One of the main technical obstacles was implementing a robust web-scraping system to collect job posting data. Initially, the workaround was to create a static database (`vagas.json` and `cursos.json`) so the core analysis and optimization functionality could be validated. Later we developed an API to enable web scraping and thus produce a higher-quality MVP. Another technical challenge was the orchestration of phases — since each phase depends on the quality of the previous one, we had to build a dependency chain that works robustly, consistently, and with high quality.

On the business side, the most notable challenge was differentiating the product in a market dominated by major players such as Gemini and ChatGPT. We overcame this by focusing on ImpulsAI’s unique value proposition: specialization in resume screening, abstraction of AI complexity, and delivery of a complete career-preparation solution that goes beyond simple text generation.

### Technical & Design Decisions and Their Trade-offs

---

The project was conceived with the help of AI and *prompt engineering*, used as a supporting tool rather than a sole decision-maker. This ethical approach ensured strategic decisions were made by the team while AI accelerated documentation and prototyping. For more details, see the [Technical Documentation](docs/technical_doc.md).

#### Key technical decisions:

* **Built a custom API for web scraping:** Developing an in-house API for web scraping was costly but essential to add technical value to the MVP.
* **BDD methodology:** Adopting Behavior-Driven Development (BDD) for writing requirements and test cases proved crucial. This keeps the focus on user value, aligns teams, and improves communication.
* **Data storage:** Using static JSON files for the MVP was a conscious trade-off to speed up development and avoid the initial complexity of a relational or NoSQL database.
* **Transition from monolithic to client-server architecture with decoupled backend:** Moving to a client-server model was a necessary step to enable the MVP and integrate with the developed API.

### Lessons Learned and Next Steps

---

Developing this initial version allowed us to validate the best technical architecture for the project. BDD taught us to keep focus on user value, manage scope, prioritize product quality, and differentiate in a competitive market. Another key lesson was the importance of having technical documentation prepared in advance as a guideline for development and as an artifact that supports technical and business decisions.

**Planned next steps (out of current scope):**

* Add support for building resumes from scratch via forms.
* Integrate the platform with job board APIs for automated job discovery.
* Develop a dashboard to track applications.
* Support multiple languages.

### Our Team

---

Our team brings together professionals with diverse experience and technical backgrounds, creating a perfect *symphony* between development, data and business.

* **Ithalo Araujo** ([iras@cin.ufpe.br](mailto:iras@cin.ufpe.br)) — Product Manager: business analysis, requirements specification, technical documentation, diagrams, presentations and reports.
* **Maria Eduarda de Lima** ([melg@cin.ufpe.br](mailto:melg@cin.ufpe.br)) — Developer & Data Engineer: ETL processes, API development for web scraping, and CI/CD pipeline implementation.
* **Rafael Moura** ([rnm4@cin.ufpe.br](mailto:rnm4@cin.ufpe.br)) — Developer: responsible for front-end and back-end implementation.

### How to Contribute

---

ImpulsAI is an open-source, collaborative project. **Contributions are always welcome** — whether suggestions, bug reports or feature additions. For details, please see our [contribution guide](docs/contribute.md) or open an issue in the repository.

### How to Build

---

To set up and run the project locally, follow the prerequisites and installation steps in the [build file](docs/build.md). The process involves cloning the repo, installing backend and frontend dependencies, and starting both servers in separate terminals.

### Useful Links

---

* [Pitch](): [https://docs.google.com/presentation/d/1phDWPOVSU1KECS024X2yv7FsJcmgeZDKwAhK-1YP96k/edit?usp=sharing](https://docs.google.com/presentation/d/1phDWPOVSU1KECS024X2yv7FsJcmgeZDKwAhK-1YP96k/edit?usp=sharing)
* [Final Report](): [https://docs.google.com/document/d/1lUiZjpNS5G4i2UkEL7y0fX70t2_k2-4sXENNvUUlH0E/edit?usp=sharing](https://docs.google.com/document/d/1lUiZjpNS5G4i2UkEL7y0fX70t2_k2-4sXENNvUUlH0E/edit?usp=sharing)
* [Full Technical Documentation](docs/technical_doc.md)
* [AI Design Artifacts](docs/ai_design_artifacts/)
* [C4 Diagrams](docs/diagrams/)
* [Prompting](docs/prompt_engineering/)
* External API: [https://github.com/melg88/api-jobs-courses-impulseAI/blob/main/docs/API_CONSUMER_GUIDE.md](https://github.com/melg88/api-jobs-courses-impulseAI/blob/main/docs/API_CONSUMER_GUIDE.md)
