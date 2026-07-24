# Developer OS Development Philosophy
_"If this project had 50,000 users two years from now, would I still be happy I made this decision?"_

## Q: Why did you choose React over Angular?
A: I wanted to take advantage of the UI Library and shallower learning curve to develop the frontend of Developer OS. I've read that it is extremely flexible, has a massive ecosystem, and supports SaaS projects. It seemed to align more closely with the targeted end goal of the project. I chose React because of its component-based architecture, flexibility, extensive ecosystem, and strong adoption for modern SaaS applications.

## Q: Why Node over ASP.NET core?
A: Initially, I decided to utilize ASP.NET as a backend development tool over Node based on performance differences I read about between the two. Upon further research, I have learned that Node integrates incredibly well with React. Using TypeScript throughout the stack reduces language context switching and allows shared concepts, tooling, and types between frontend and backend. No context switching is required because both React and Node.js utilize TypeScript. This means full stack development becomes more efficient.

There is also a ton of documentation and support for Node: the ecosystem is massive. Considering this project more closely aligns with a startup, SaaS, and full-stack development, Node seems like the correct choice. Plus, the future goal of AI Integration into the application aligns closely with using a React+Node.js Full-Stack. HTTP APIs are easily utilized via this framework and the easy passage of JSON files from one backend to another. The goal of this project is to utilize AI Models, not train them. For this reason, Node seems to be sufficient.

From what I have read, updates to SDKs are usually more readily available to backends that utilize Node.js instead of ASP.NET. Many modern AI SDKs and developer tools release JavaScript/TypeScript support first, with .NET support sometimes arriving later. Since Developer OS plans to integrate existing AI services rather than build machine learning models, the JavaScript ecosystem aligns well with the project's goals.

Considering support, rapid integration, and full-stack alignment, I think Node.js is the preferred choice for this project.

## Q: What is npm, pnpm, Turborepo, and Nx? Why would you use one over the other or some combination?
A: _npm_ is the default package manager that ships with Node.js. _pnpm_ is also a package manager, but it has advantages over _npm_. For instance, _pnpm_ stores package contents in a global content-addressable store and links them into projects instead of duplicating files. Thus, _pnpm_ is a direct replacement for _npm_ that allows a project to become more lightweight and efficient. Processing time and total storage requirements are cut down when using _pnpm_ over _npm_.

On the other hand, Turborepo is _not_ a package manager: Turbo runs tasks. Turbo understands dependency graphs, so if an API is the only thing that changes in a project, Turbo doesn't need to rebuild the UI. This yields _huge_ speed increases. With Turbo's caching capabilities, building projects is _much_ faster. Turbo is lightweight, and requires little configuration. Turborepo allows Developer OS to grow into multiple applications and shared packages without significantly increasing build complexity.

Nx rivals Turbo. It is much larger and provides more features than Turbo. The downside of Nx is the steep learning curve.

This project will utilize _pnpm_ workspaces with _Turborepo_ for task orchestration.. While I do like the potential of _Nx_ in terms of features and possibilities, I think the ideology of _Turborepo_ more closely aligns with what this project is: a small startup-like SaaS platform.

## Q: Why use a monorepo at all?
A: Shared code across platforms becomes easy. There is one source of truth. Large changes to the app are consistent across front-end, back-end, and platforms. No need to update multiple repositories when making changes to one element of the overall application. Dependency management is also easier with a monorepo than several independent, isolated repositories. It is also easier to explain the project to someone else down the road if that ever occurs. New developers can more easily hop in on projects that utilize monorepos. Large architectural changes and refactoring code becomes easier.

The downsides are somewhat obvious: monorepos are _massive_. Cloning a project may take significantly longer. The repository may contain more tooling, so the complexity requires more package installation. Teamwork becomes difficult as changing any one section of code could impact another team's work. This is a non-factor on this project considering I am currently the sole developer.

It is interesting to note that Google and Meta utilize a monorepo. These are some of the largest tech companies in the world with _massive_ code bases, and they are able to make monorepos work.

The monorepo design allows frontend and backend architecture, shared contracts, CI/CD, package management, and developer tooling all in one codebase. Considering this project will become one application consisting of many smaller applications, the monorepo seems to be a good design choice.

The primary benefit is not repository consolidation itself, but maintaining shared boundaries between related applications.

## Q: Why the focus on widgets instead of pages?
A: The question is really asking about how the composition of the project. In the future, I see the benefit of having several re-usable components that are stylistically aligned. I think this will provide a clean, uniform user experience. While the development velocity of pages may be faster, the potential duplicity of elements I foresee in this project leads me to think implementing reusable widgets is a good idea.

I do think that some combination of widgets, independent pages, and other components will eventually trickle their way into the project, though I will be looking to implement widgets whenever I can in the interest of not rewriting code, stylistic uniformity, and generally learning how to develop quality widgets.

## Q: Why PostgreSQL instead of MongoDB or some other DBMS?
A: I would choose PostgreSQL over MySQL due to the richness of features the former is said to have over the latter. On the surface, SQLite doesn't seem to provide the scaling that I anticipate this project could reach i.e. SQLite is primarily used for smaller projects and I foresee this project evolving into something that requires a more robust DBMS. On the contrary, something like Cassandra sounds like overkill. I could see Redis and/or ElasticSearch being useful in some capacity, just not at a primary database. 

In the interest of learning the skill set of a professional software developer, I think PostgreSQL will allow me to learn skills that are highly transferable. While MongoDB could work as it utilizes JSON files for data transfer and storage, I am setting out to learn PostgreSQL with the potential in the future to implement DBMS Tooling such as MongoDB, Redis, and/or ElasticSearch if the project seems to call for it.

## Q: Why REST first instead of GraphQL? Vice versa? Are there other alternatives?
A: Simplicity. REST maps naturally to HTTP, has decades of support, and provides easy debugging. Over-fetching is a drawback that I am considering, as well as under-fetching, though the alternatives are said to be overly complex i.e. GraphQL. REST has a simpler security model for an initial architecture. REST is said to have a shallower learning curve, predictable performance, excellent caching, and simple design decisions. 

I could see an initial project launch with REST API integration followed down the line by some layer of GraphQL if necessary. Then, if the project is begging for more in terms of database management, I would dive into management utilities like WebSockets or Server Sent Events. I found a great quote online:

_"REST-first is like learning manual transmission before driving an automatic: it exposes the mechanics. GraphQL is incredibly powerful, but it can hide some important fundamentals."_

It is this ideology that leads me to think REST before anything else is a good personal choice.

### _"Everything is a package until proven otherwise."_

### _"Developer OS will prioritize proven, maintainable technologies over novelty. New technologies may be adopted when they provide clear value, but complexity must justify itself."_

### _"I finally found a project that I think I can sit down, sink my teeth into, and do deep work on to develop and make impactful decisions that will ultimately determine the end user experience."_