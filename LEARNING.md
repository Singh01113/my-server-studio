# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** This coaching chat, from local setup through agreed scope and pre-launch checks. Draft; not yet reviewed for publication.

## Try · classroom example

Learner-reported observation: at <https://calc.mywebclass.org>, tried `8 + 5`,
predicted `13`, saw Browser Result `13`, API Result `13`, and “Results match.”
Learner explanation: “This shows that JavaScript and the FastAPI backend agreed
on the calculation.” This is the classroom example, not the learner's deployment.

Help received: AI had demonstrated `6 × 7` earlier and requested a separate
learner observation. AI drafted this summary from the learner's report.

## Prediction

Learner quote, before the deployment plan explanation: “I think when someone
enters my calculator URL, the request goes to my DigitalOcean server through
HTTPS on port 443. Traefik checks the hostname and forwards the request to the
calculator's Docker container through the hosting-web network. The calculator
then sends the response back to the browser.”

Help received: AI prompted the learner to consider the hostname, Traefik and
Docker container. After this response, AI added that DNS supplies the server
address and Traefik handles HTTPS. Those additions are AI explanation, not
learner words.

## Check interpretation

I ran the prepared fast checks before deploying my calculator. Black and Pylint passed, and 91 automated tests passed. Two browser E2E tests were not run because Docker Desktop wasn't running on my laptop.

These results showed that the code passed the available local checks, but they didn't prove that the calculator would work on my server. After deploying, I verified that HTTPS worked, the calculator API returned correct results, and all four existing containers were preserved.

I still need the full browser E2E tests to pass in GitHub CI.

## Browser observation

I opened my deployed calculator at https://amman-calc.134-209-120-185.sslip.io and tested 9 × 4.

Before clicking Calculate, I expected the answer to be 36. After clicking the button, the Browser Result showed 36 and the API Result also showed 36. The page displayed "Results match."

This confirmed that my calculator was accessible through HTTPS and that the JavaScript calculation agreed with the FastAPI backend for my test.

This was different from the classroom example because I was testing the calculator deployed on my own DigitalOcean server.

## Keep decision

I decided to keep the calculator deployment because it passed the HTTPS and API checks, and my own browser test returned the expected result.

The deployment also preserved all four existing Docker containers, so I didn't need to change or replace my other services.

I still need to finish the GitHub pull request and run the full browser E2E tests through CI. If those tests fail, I'll review the errors and revise the work before merging.

## Review

I reviewed the learning summary and checked it against the tests and observations I actually completed.

I used ChatGPT and Codex to help understand the assignment, inspect my server, run the prepared checks, and draft the documentation. I also tested the classroom calculator and my deployed calculator myself.

The deployment evidence confirms the successful launch, HTTPS verification, and preservation of my existing containers. The full browser E2E tests and GitHub CI are still pending.

I reviewed the explanations to make sure they reflect what I did and learned. I will check the final changes before committing them to GitHub.

## AI work and next step

AI helped me set up my local project, understand the assignment, inspect my DigitalOcean server, and prepare the deployment plan. I agreed to use my existing Docker network and Traefik setup so my other services would remain intact.

The prepared fast checks passed Black, Pylint, and 91 tests. Two browser E2E tests were not run locally because Docker Desktop was unavailable.

I successfully deployed the supplied calculator using `python3 studio.py launch`. The deployment passed the HTTPS, image verification, API, and existing-container preservation checks. I also tested 9 × 4 myself and confirmed both results displayed 36.

GitHub Issue #1 was created, and the deployment evidence was exported to `studio/evidence.json`. ChatGPT and Codex assisted with the instructions and documentation, which I reviewed against my actual results.

My next steps are to commit and push my changes, create a pull request, verify the full GitHub CI tests, and merge the completed work into `main`.
