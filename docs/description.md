---
layout: default
title: Job Description
permalink: /job-description
order: 4
---

My time at CDS was split between two projects:
* The [`EnerGuide API`](#energuide-api---github-link), a project for National Resources Canada
* The [`Track web security compliance`](#track-web-security-compliance---track-web-tracker) project for TBS Cyber Security.

# EnerGuide API - [Github Link](https://github.com/cds-snc/nrcan_api)

This project was to help expose data collected for the EnerGuide for New Houses project that National Resources Canada initiated in 2006.

They have a large collection of data colleced during housing inspections, and arrangment to provide slices of that data to interested parties (such as energy companies and academics), but a need that was identified to help an initiative of theirs to provide home owners with information about their home was an API to expose this data.

CDS partnered with NRCAN to help build this API, and I was part of that team.

The product was split into two parts, and ETL process to transfer and transform the data to help the second part, which was an GraphQL API.

The ETL process was what I, along with a few others, were responsible for building out. The pipeline was built in Python, and loaded the data into a MongoDB database that the API pulled from.

# Track web security compliance - [Track-web](https://github.com/cds-snc/track-web), [Tracker](https://github.com/cds-snc/tracker)

During my second term after the EnerGuide API project had wrapped up, I was put onto a project to security compliance of websites owned by the Government of Canada. This project was based off of [work by 18F](https://github.com/18F/pulse), an organization that is part of the United States government with a similar role as CDS.

[New policy](https://www.canada.ca/en/treasury-board-secretariat/services/information-technology/policy-implementation-notices/implementing-https-secure-web-connections-itpin.html) was released in tandem with the project outlining what security practices site owners needed to impliment, and the dashboard we built measured and presented that data.

The dashboard was a combination of two different coordinating applications, `track-web` and `tracker`.

`track-web` is a Python application using the Flask web framework that served the results to users, it was the dashboard.  
I was part of some of the backend work on this part of the project, but primarily this was the responsibility of the other developer on the project.

`tracker` is a Python application that given a set of domains, will make and measure connections to them to determine their compliance.  
This part of the project was my primary responsibility. I was tasked with refactoring to move away from the part sof the original source that we didn't like, and changing the processing logic to fit our compliance criteria.

---

Both of these projects leveraged my existing proficiency with Python, but both also required an understand of software packaging and deployment that I completely lacked previously.  
Docker is a great technology that we used to help satisfy both of these needs.

<div class="next-page">
    <a class="next-page-link" href="tech">About the Tech</a>
</div>
