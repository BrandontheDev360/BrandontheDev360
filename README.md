# 👹 Brandon Nguyen

**`< Software Engineer @Cigna />`**

 <h3>👨‍💻 Brandon's Coding Journey</h3>
  Hello nice to meet you, my name is Brandon Nguyen, and I'm a Java Software Engineer. My story started out as a lost college IUPUI undergraduate majoring in Psychology. After the realization I didn't know what I wanted to do with my career, so on a whim I attended an introductory course at Eleven Fifty. After that I discovered my new found appreciation for Computer Science and Web Development at Eleven Fifty Academy. Which has led me into the current technological journey I am on. I hope to inspire others aspiring software engineers with my own journey, progress, and help others learn from my failures. 



PR Description:

This PR implements an aggregation-based solution for dynamically filtering and processing group health plan records. The new pipeline computes a planYear from the planEndDate (stored as a String) and a modifiedDate (choosing between updatedDate and createdDate). Using the $setWindowFields stage, it partitions documents by groupHealthPlanName and groupHealthPlanNumber and computes the maximum plan year within each group. This allows the pipeline to filter out older records when duplicate group health plan entries exist—retaining only the current year record per group. In addition, the solution supports optional filters (e.g., marketSegment, region, minPrice) and returns a paginated result as a Page<PlanInfo>.

Change Log:

Dynamic Filtering:

Added support for optional request parameters (marketSegment, region, and minPrice) using a dynamic $match stage.
Computed Fields:

Introduced planYear field by converting the planEndDate string to a Date and extracting the year.
Added modifiedDate field which uses updatedDate if available, otherwise falls back to createdDate.
Aggregation Enhancements:

Implemented $setWindowFields to partition records by groupHealthPlanName and groupHealthPlanNumber and compute maxPlanYear for each group.
Added a filtering stage that retains only documents where planYear equals the computed maxPlanYear, ensuring that only the current year record is kept when duplicates exist.
Pagination:

Integrated pagination support via skip/limit stages and implemented a separate aggregation for total count.
---

### 🧰 Languages and Tools

<img align="left" alt="Java" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg"/>
<img align="left" alt="Spring" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/spring/spring-original.svg" />
<img align="left" alt="TypeScript" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-plain.svg" />
<img align="left" alt="HTML" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-plain.svg" />
<img align="left" alt="CSS" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-plain.svg" />
<img align="left" alt="JavaScript" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-plain.svg" />
<img align="left" alt="React" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" />
<img align="left" alt="NodeJS" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" />
<img align="left" alt="GitHub" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" />
<img align="left" alt="Git" width="40px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" />
<br />

#
