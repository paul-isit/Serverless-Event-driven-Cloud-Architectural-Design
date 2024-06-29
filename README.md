# Serverless-Event-driven-Cloud-Architectural-Design
This report provides alternative solutions to develop a design for hosting a scalable highly available web application using cloud applications such as Amazon Web Services.

The details of the scenario are as follows:
The Photo Album application you developed has met with amazing success and needs to be further
developed to meet increasing demand. In particular, the following problems/requirements have been
identified by the company:
1. Where possible the company would like to use managed cloud services to minimise the need for
in-house systems administration. Photo and other media will be stored in AWS S3.
2. The company is not sure how demand for its application will grow in the future but over recently
it has been doubling every 6 months. It expects this trend will continue for the next 2 or 3 years
at least and it wants the architecture to be able to cope with this growth.
3. The current system EC2 instances are running on t2.micro. The compute capacity is regularly
exceeding the 80% performance limit with 6 instances running. The desired load needs to
decrease to between 50 and 60%. Ignore this requirement if your solution does not involve EC2.
4. The company would like to adopt a serverless/event-driven solution.
5. The relational database is relatively slow and costly to run. Given the simple table structure, the
company would like to explore more cost-effective options.
6. The application has had wide uptake around the world but response time in countries other than
Australia has been relatively slow. Global response times need to be improved.
7. It is expected the system will be extended to handle video media in the future.
8. The media can be uploaded by users in all sorts of formats. The company would like various
versions of media to be automatically produced (e.g. thumbnails, low resolution versions suitable
for mobile phones, or video transcoding). The process for reformatting/transcoding/reprocessing
media should meet the following criteria:

a. When a media item is uploaded to the S3 bucket, the creation of these alternative versions
should be triggered automatically. Transformed media will also be stored in S3.

b. The architecture for processing media should be extensible. For example, in the future it may
be desirable to add the ability to automatically identify tags in photos using AI.

c. Different processing services should be able to be run on the most suitable platform – e.g. EC2
instance, Lambda, or other AWS managed services. Given cost and performance constraints it is
assumed that all services will be provided in the AWS ecosystem.

d. The reprocessing/reformatting of media is often a time-consuming task. The architecture should
be designed so that the application does not become overloaded and is effectively decoupled.
For example, multiple ‘worker’ nodes can process transformation jobs that have been placed on
a queue. The worker nodes may specialise in particular tasks. For example, one node may
specialise in video transcoding which is much more processor and memory intensive than
reformatting a photograph
