# 👹 Brandon Nguyen

**`< Software Engineer @Cigna />`**

 <h3>👨‍💻 Brandon's Coding Journey</h3>
  Hello nice to meet you, my name is Brandon Nguyen, and I'm a Java Software Engineer. My story started out as a lost college IUPUI undergraduate majoring in Psychology. After the realization I didn't know what I wanted to do with my career, so on a whim I attended an introductory course at Eleven Fifty. After that I discovered my new found appreciation for Computer Science and Web Development at Eleven Fifty Academy. Which has led me into the current technological journey I am on. I hope to inspire others aspiring software engineers with my own journey, progress, and help others learn from my failures. 

// Step 1: Add $setWindowFields for ranking logic
Document setWindowFieldsDoc = new Document("$setWindowFields", 
    new Document("partitionBy", new Document("groupHealthPlanName", "$otherEntityInfo.groupHealthPlanName")
                                    .append("groupHealthPlanNumber", "$otherEntityInfo.groupHealthPlanNumber")
                                    .append("orgId", "$otherEntityInfo.orgId")
                                    .append("carrierCode", "$otherEntityInfo.carrierCode"))
        .append("sortBy", new Document("otherEntityInfo.referenceYear", -1)  // Sorting by referenceYear
                                .append("modifiedDate", -1))  // Sorting by modifiedDate for recent data
        .append("output", new Document("rank", new Document("$rank", new Document("window", new Document("documents", Arrays.asList("unbounded", "current"))))))
);

// Step 2: Perform a $group to simulate DISTINCT, keeping the most recent record for each partition
Document groupDoc = new Document("$group", new Document("_id", new Document()
        .append("groupHealthPlanName", "$otherEntityInfo.groupHealthPlanName")
        .append("groupHealthPlanNumber", "$otherEntityInfo.groupHealthPlanNumber")
        .append("orgId", "$otherEntityInfo.orgId")
        .append("carrierCode", "$otherEntityInfo.carrierCode"))
    .append("maxReferenceYear", new Document("$max", "$otherEntityInfo.referenceYear"))
    .append("latestRecord", new Document("$first", "$$ROOT"))  // Keep the first record (most recent)
);

// Step 3: Optionally, use $project to flatten the grouped fields
List<AggregationOperation> operations = new ArrayList<>();
operations.add(new CustomAggregationOperation(setWindowFieldsDoc));  // Add the windowing operation first
operations.add(new CustomAggregationOperation(groupDoc));  // Group the data for distinct results

// Project the necessary fields from the latestRecord (or root document)
operations.add(project()
    .and("_id.groupHealthPlanName").as("groupHealthPlanName")
    .and("_id.groupHealthPlanNumber").as("groupHealthPlanNumber")
    .and("_id.orgId").as("orgId")
    .and("_id.carrierCode").as("carrierCode")
    .and("maxReferenceYear").as("maxReferenceYear")
    .and("latestRecord").as("latestRecord")  // This keeps the full document from the latest record
);

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
