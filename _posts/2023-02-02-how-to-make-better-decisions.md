---
layout: post
title: "How to Make Better Decisions"
date: 2023-02-02 21:00
description: A short article on decision making I wrote for someone I mentor at Pipeworks 
categories: Lead-Development
---

# How to Make Better Decisions

## Intro

There are a number of [mental models](https://fs.blog/mental-models/) one can use to improve decision making such as an [Eisenhower Matrix](https://en.wikipedia.org/wiki/Time_management#The_Eisenhower_Method), or [Inversion](https://fs.blog/inversion/). To find one that works for you you're going to need to iterate and try them out. There's no one method that will work for everyone, and any method will need refinement to you as the individual. There is also no mental model that fits all situations. The following is an overview of a high level process, they key part is to not spend more time than is needed in making any decision. 

## How Quick Can You Make a Decision

Step one is to assess how much time I need to spend making the decision. Starting with a decision matrix with axis reversible vs scope of work you should be able to, with in a matter of seconds, assess this time. 

Example 1: *Should we add a bug about a missing UI element?*

This is a quick decision. Yes. There's minimal work in adding the bug and worst case, we can simply close it out. Not adding the bug sends the signal that we care more about the noise in our bug tracker than we do the quality of the game. 

Example 2: *Should we hire this person?*

This decision is both not easily reversible and has a high scope of work. Lots of things kick into motion for the company and the individual after this decision is made. This is where you want to take some time, at least a full day to mull over your thinking. 

Once you've assessed how much to put into the decision it's time to start to digging into the details. What context am are you missing? Do you understand the impact?  Since you were unable to quickly make a decision in step one, it means there's missing information. Whether it's pen and paper or a text editor, it's time to start clarifying your thinking outside of your head. You simply won't be able to evaluate complex systems in isolation. Even if you could, documenting your thought process will help you refine it later, additionally, it allows you to look back at previous decisions to learn from them. 

## Example

Let's run through a contrived example to see a potential decision process you might have. 

It's time to start the next version of your game and you know that during preproduction you need people who can excel in a fast decision making, rapid prototyping, highly collaborative environment. However, the people you know to be the best fit are supporting your live ops team. 

* Do you pull the live ops people and backfill?
* Do you have someone else start the new project with an assist from the live ops team?
* Do you have someone else start but with no help from live ops
* Something else?

You start by inverting the question, rather than who should start the next version, you ask, who needs to support the live ops game, and what happens if they're not there. When you ask this question you're trying to identify gaps in your understanding of the impact of the decision. 

With impact assessed you start to ideate and enumerate your options. To evaluate each option you make a quadrant diagram with Impact vs Effort and plot your options. The image below is a hypothetical Impact vs Effort matrix, where A-F are possible decisions you are evaluating. 

[![Example of an impact vs effort matrix with options plotted as dots](/assets/images/how-to-make-better-decisions/impact-vs-effort-article.jpg)](/assets/images/how-to-make-better-decisions/impact-vs-effort.jpg)

To start, focus on the solutions that will have high positive impact and low effort. For instance, maybe you can redefine the scope of work on the live ops side to where it can be delegated to a trusted vendor. This frees up your live ops lead to begin focusing on the next game. Assuming the trust level with the vendor is sufficiently high and they're already on the project, the effort to make the change might be low. 
For each option in the low effort, high impact category, began to think about the second and third order ramifications. In the example above, let's say you pulled the vendor to take over live ops. What were they working on that's no longer having effort put into it? What were they going to work on next? What's the impact there? Was there dependancies in the work that are now going to become blockers? Maybe they aren't able to get permissions to effectively support live ops. Or are unable to get equipment. 

We might not be able to identify all the gaps in our initial assessment of a situation or solution, which is why we need to spend additional time evaluating how they play out. Once you have a few options you like, it's time to run them by others. Never make decisions that will impact others in isolation. We all have blind spots and biases, working with others helps us identify them. 

Now the last step. Pick one solution and live with the fallout.   

## Feedback on Ideas

In the example above, we saw the need to get feedback from others. This step happened towards the end, but it can, and should, happen multiple times throughout the decision making process. One method or eliciting feedback when wanting to effect change is called [Nemawashi](https://en.wikipedia.org/wiki/Nemawashi). Decisions affect change, they create branches, and Nemawashi is a great way informally gain new perspectives on these branches. 

Another avenue for getting feedback is to discuss your situation with proposed solution and mitigation plans with someone who has been in a similar position, or is higher in the org than you. While it's great to get their insights, keep in mind that the decision is ultimately up to you. If it wasn't, you wouldn't be the one making it. Don't take their feedback blindly, make the decision and own the results. 

There are times when you won't be able to get feedback from others, say late night trying to finish a release build to QA, and you have to make an "executive" decision. But and "executive" decision is no different than any other. Going through a process, you have information that tells you why this is the best decision given the situation. And if you believe the decision is the right one by the project or company it's the right one. You didn't flip a coin, you thought critically about your choices. While it sounds flippant to say, if you are in an org that focuses on the outcomes of your decisions rather than your process, your growth will be limited. 

## Wrapping up

This whole process may only take a few minutes or hours. For a big decision such as a new hire, maybe a full day. Remember, the time you spend in making the decisions is proportional to the impact of getting it wrong. Given that we're in game dev, and no one's life is on the line, try not to stress too much. Also, most of us are not at the executive level, our decisions have rather small chance of resulting in layoffs or the cancelation of a project. It's hard for a single decision to have that level of impact, those results tend to be from a number of small decisions. 

With all this there are two perils to be aware of: [decision fatigue](https://en.wikipedia.org/wiki/Decision_fatigue) and [analysis paralysis](https://en.wikipedia.org/wiki/Analysis_paralysis). It's easy to get wrapped up in wanting your decisions to be perfect, but don't let perfect be the enemy of good. You will never make perfect decisions and it's not a scorecard; number of "good" vs "bad" decisions. You will always make the best decision you could with the information you have at that time, with hindsight you will always be able to reason about a "better" decision. The point of a processes is to allow us to evaluate that information more effectively and over time refine our ability to make decisions with more confidence. 

## Further Reading

* [Practical Ideas Better Decisions](https://fs.blog/practical-ideas-better-decisions/)
* [Decision Anatomy](https://fs.blog/decision-anatomy/)
* [Decision Matrix](https://fs.blog/decision-matrix/)
* [Smart Decisions](https://fs.blog/smart-decisions/)
* [How to Make Great Decisions Quickly](https://hbr.org/2022/03/how-to-make-great-decisions-quickly)
* [The Importance of Small Decisions](https://www.amazon.com/Importance-Small-Decisions-Simplicity-Technology/dp/0262039745)
* [Good Strategy Bad Strategy](https://www.amazon.com/Good-Strategy-Bad-difference-matters/dp/1781256179/)
* [Thinking Fast and Slow](https://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555/)

