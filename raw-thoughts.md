applications: deployed in Kubernetes.
Pods can be scaled up and down, depending on the traffic load.

Kubernetes commands to interact with pods or log in to pods.
A console or a dashboard to see the status of all pods. different environments like staging and sandbox and production and development.

developer productivity: making it easy for developers to create a playpen on staging or development so that testing and proof of concepts can be built easily and turn around times are less from idea to implementation.

pod health: things like current memory consumed, CPU percentage, and so on.

deployments: quick way to see what was deployed and when, quick rollback times,
rollout by geography, percentage, time based rollouts to minimize severity.
hosting in different regions to ensure reduced latency.

levels of severity and how to define it: a subset of users are unable to achieve a main goal.

how to declare a SEV and who to keep informed.
first order of operation when SEV is declared:
1. pull in the right stakeholders.
2. check if any deployments or configurations in the recent past.
3. conservative rollback if required.
4. communicate that you're investigating
5. observer any dashboards, logs.
6. form a hypothesis.
7. postmortem: client-facing report, 5 why analysis, 
questions to ask in post-mortem:
    Incident timeline and walkthrough
    could the time to recovery have been halved?
    could the time to detection have been halved?
    how were we notified of this?
    was there a feature flag that protected this rollout?
    was there a task in the backlog that might have prevented this? why wasn't it prioritized?
    could the impact have been worse? did we just get lucky?
    any other tools that might have helped us?
    what action items do we need to take and how do we prioritize it?

Oncall responsibilities:
1. deployments
2. handle any active SEVs
3. handle any customer questions on customer forums
3. ensure system health: periodically monitor dashboards
4. system SLO: is our system keeping upto date with the different SLOs that we promise.
if we promise five 9s uptime, why did it drop below that threshold? was it due to some incident? how are we ensuring that we will recover from this?
5. are there any upcoming events oncall needs to be aware of? like some team deploying something, a dependent team doing a migration? a deploy freeze?
6. are there any upgrades or generic maintainance needed to be done? how are we handling that?

Dashboards: [i have experience with Datadog]
1. to monitor 200 responses in endpoints over time. if there is an unexplained dip, it is a cause for concern
2. generic QPS monitoring.


automated monitors that should alter oncall either via the pager or slack or email:
1. based on priority: 'warn' can be slack/message only and 'triggered' can be pager
1. high 5xx rates of certain endpoints
2. high 4xx rates - this can mean it is a targeted attack or someone is sending us incompatible requests for some reason. it can also be normal for some endpoints
3. no requests - maybe be a upstream issue. for some reason our server stopped getting requests.
4. endpoint latency to track.

it is important to set thresholds. like it may be normal to see 2 or 3 5xx errors in a second, but it is important to set thresholds so we do not trigger oncall too much with false positives.

1. how to set up automated systems that trigger when some dependent packges go out of support or flag a system vulneratbility. 

1. logging:
different levels of logging. what logs are important to have and how to have them?

1. do not add many systems as dependencies especially if you know it's undermaintained. do a thorough analysis of dependednt systems - who owns it, what is the community's stance about it, when was it last upgraded, is it actively in maintaince, does it follow standard guidelines.

Test Coverage:
it is important for all production grade code to have unit tests, integration tests, e2e tests and acceptance tests. there are code coverage tools that test coverage. if a pull request is added with new code, how does it perform with respect to branch coverage, overall coverage. if it fails coverage rules, the pr shouldn't be allowed to merge.

Linters are required to ensure code quality. it is possible to have git commit hooks that check that all lint rules pass before a commit is made. this saves time for the developer and helps them ensure code style and quality is maintained.

it is possible to enable linters in IDE of choice to help with coding.

if you're having a product that other developers use, it is important to maintain clarity in tech ref docs or developer docs. it is important to maintain consistency across different APIs, methods or options so that it is intuitive for developers. ensure that your docs are consistent with your code. it is possibel to find documetnation generation tools that generate docs from code.
if you're throwing errors, ensure errors are consistent for similar kinds of issues - so handling on their side is easy.

to ensure maximum quality of code being checked in, there can be automated build systems. Automated CI/CD pipelines:
1. that run linters
2. runs tests
3. ensures code coverage
4. ensures feature flag is added if important change
5. if there is a failure, is clean interface to link to the line of failure in code or links to logs.
6. approvals from team mates.

configure owners for code repositories/files or lines of code so that the right people are tagged to apporve a change to the file.

git tools to make working in repositories easy.
git cherry pick to cherry pick a certain commit and apply it to a different branch.

have design docs, 1 pagers to explain engineering designs and decisions before starting an important project and ensure it is approved by teammates.

access control like app owners and database owners. have adming access and read access as required.

technical communication - oral and verbal. ensuring you communicate succinctly - make the request clear.

one public slack per team, to ensure we have visibility.
make FAQs for people coming into your team with questions.

AI productivity tools: git worktrees locally to work on separate features. you can have multiple versions of the repository checked out locally and switch between each as required. and have claude or any other AI agent working on them locally.

style guide: do not use generic names like utils or utilities for directory names. these are breeding ground for it to become a dump yard of unrelated things later.

encapsulation or separation of concerns for different things.

build tools for things to work together.
we used turbo and yarn and other build tools.

try to create workflows or systems - ones that can work together. it could be trying to connect ticketing systems with the communication tool of choice, that way if a customer makes a request you can automatically create a ticket from there and so on.