# Building internal tools

## Ideas

### Tech perspective

- One view per resource: this helps keep the domain model clear and equal in everyone's heads (ubiquitous language).
  - Alex found this point confusing: clarify that this is about resources that eventually "become" other resources: a request becomes a booking, and they should have their own, separate UIs instead of sharing one.
- Keep the application very close to the data model and the database.
- Try to imagine the application in the long term:
  - Is the amount of UI in the app likely to become very large, due to an extensive model or a complex process?
    - Then choose battle-tested, batteries-included tools that don't require a lot of effort to use.
    - Adapt your case to the tools available instead of trying to optimize for minor interactions.
  - Are processes likely (or even planned) to change after a year or two?
    - If so, then choose UI tools that are unlikely to change, so that you only need to handle the changing processes, and not a changing toolset.
- Goes for all applications:
  - Keep the logic in the backend as much as possible. Business logic can creep into the UI in many ways:
    - Through fetching different resources together and mixing them up in the client.
    - Through running consecutive actions in the frontend that should be one backend transaction.
    - Marcus has questions about this: is it possible to keep absolutely all business logic out of your application?

### Product perspective

- Tools are automation. Rule of thumb: do it manually three times before automating it. That way, you'll have a fair idea of what it is supposed to do (which is the hardest part); you know whether it's predictable enough to be automated; and an how often it will come up. [Link](https://news.ycombinator.com/item?id=4766714)
- I think before you start automating you business and processes you first need to know if your product will get any traction. Spending the time on making sure you have the best possible MVP is the most important thing, IMO. You may be launching a lot of tasks manually and modifying the database directly from the console at first but so be it. The fact is that creating internal tools is very expensive and only indirectly provides benefits to your product. [Link](https://news.ycombinator.com/item?id=4766774)
- If customers and employees interact using the same resources (i.e. the resources are both present on the customer-facing apps and the internal tools) then consider making your employees access those resources using the toosl the customers use, instead of the internal tools. This helps keep the internal UI at a minimum and makes your employees share the experience of the customer.

## Possible existing stacks

- [ActiveAdmin (Rails)](https://activeadmin.info/)
- [Retool](https://retool.com/)
- [Forest Admin](https://www.forestadmin.com/)
