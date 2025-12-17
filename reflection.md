# Reflection

## Confidence and Uncertainty in the Design

The part of this project that I feel most confident about is the overall structure of the system and how the cloud services connect to each other. Throughout this course, we practiced working with virtual machines, Flask applications, managed databases, and serverless functions, and this project brings those pieces together in one workflow. Using a Flask app running on a Compute Engine VM as the main entry point felt familiar because it builds directly on the earlier assignment where we deployed a Flask app on a cloud VM and configured networking and firewall rules.

I also feel comfortable with the idea of separating data by type, such as storing referral documents in Cloud Storage and keeping structured referral information in Cloud SQL. This separation made sense based on what we learned about managed databases and storage services, and it helped me understand how different cloud services are used for different kinds of data.

The area I am least confident about is security and access control beyond a basic level. While the design mentions service accounts and limiting access, I'm not too confident with application-level authentication or role-based access control. I understand the importance of these concepts, but I think implementing them fully would require more experience of me. 

---

## Alternative Architecture Considered

One alternative I considered was running everything on a single virtual machine, including both the Flask application and the database. This would have been simpler to set up initially, but based on the assignment where we were comparing MySQL on a VM versus a managed database, it became clear that this approach would require more maintenance and manual configuration. Using Cloud SQL instead felt like a better choice because it reduces the amount of database management work.

---

## Future Improvements and Next Steps

If I had more time and additional cloud credits, the next step would be improving automation and reliability. For example, more checks could be added to ensure that referral documents are complete and correctly formatted before moving a referral forward. I would also want to improve how referral status updates are tracked and displayed so staff can quickly see where delays are happening.

Another improvement would be exploring different deployment options, such as running the Flask app in a container or using more serverless services, once I am more comfortable with those tools. This could help reduce costs when the system is not in use and make deployments easier.

---
