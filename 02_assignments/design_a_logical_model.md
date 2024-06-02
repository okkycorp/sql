# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Type 1 Architecture has CustomerID as the primary key and any new changes will overwrite existing data and will only reflect the latest entry, including the address.

Type 2 Architecture has unique AddressID as the primary key and retains every address entered. There can be multiple CustomerID per Address ID and therefore every address entries are retained. 

When a new address is entered, a new AddressID is created while being linked to an existing CustomerID. Therefore, the new AddressID is separate from the old AddressID, and both linked to the same Customer ID. This way, all address entries are retained and nothing is overwritten

Privacy Implications

Type 1 Architecture assume there can only be 1 address per CustomerID and therefore for privacy purposes, it does not retain older or historical data.

Type 2 Architecture creates new primary key AddressID every time a new address is entered and all linked to an existing CustomerID. This means all older entries are retained. There can be privacy issues where address changes are tracked and the customer's address history are retained (where they used to live and their location pattern).

In case of data breach, Type 1 only leak the 1 data point, while Type 2 leak all data points linked to a Customer. Therefore, Type 2 is possibly more catastrophic in terms of data breach and might require more costly insurance.
```

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Differences:
    1. AdventureWorks has a more complex schema with many more tables and relationships, focusing on manufacturing, product, and inventory management.
    2. AdventureWorks uses a more detailed Product table with additional attributes like ProductModel, ProductSubcategory, and more.
    
Changes in My ERD:
    • Depending on the complexity needed for the bookstore, I might consider adding more detailed attributes to the Book table, such as PublicationYear, Publisher, and Edition for inventory management.
    
If the bookstore grows, introducing more entities related to inventory management and supplier relationships might be beneficial.
```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `June 1, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-3-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
