# [Draft] LLMs, AI, and GEO

_Can you optimize for discovery in generative engines like ChatGPT, and how?_

This guide is an attempt to document emerging concepts and note sources that are making plausible (if not verified) claims about how to improve visibility in LLM-powered chatbots. It’s all very speculative right now.

## Definitions 📖

| Term | Definition|
| ---- | --------- |
| Large Language Model (LLM) | A predictive engine trained using machine learning on a very large body of text data. |
| Artificial Intelligence (AI) | Marketing term for LLM software that turns user prompts into answers in text, code, or media. |
| Generative engine | Chatbots such as ChatGPT (OpenAI), Gemini (Google), and Copilot (Microsoft). |
| Generative Engine Optimization (GEO) | Structuring content with the goal of increasing its visibility in LLM chatbot responses. |
| Retrieval Augmented Generation (RAG) | Method of incorporating material from outside the model’s training data into the response. |

## This field is very new ⚠️

The term Generative Engine Optimization (GEO) was likely [coined](https://arxiv.org/abs/2311.09735) by Aggarwal, et al. in 2023. It wasn’t until mid-2025 that Google started seeing significant [search volume](https://trends.google.com/trends/explore?q=%2Fg%2F11md5185sw&date=today%205-y&geo=US) for the term. This is to say the field is very new. It is also in flux and full of wild claims (e.g. “SEO is dead”). So it pays to retain your skepticism until clearer guidance emerges from providers that can be tested and validated in real-world scenarios.

## Why do LLM/AI tools matter for SEO?

The short answer is that LLM answers in traditional search engines, and LLM tools that present a chatbot interface have led to  a decline in search engine traffic referrals, especially since 2025 for .gov sites.

*	[Google users are less likely to click on links when an AI summary appears in the results](https://www.pewresearch.org/short-reads/2025/07/22/google-users-are-less-likely-to-click-on-links-when-an-ai-summary-appears-in-the-results/) — Pew Research Center (July 22, 2025)

## Topics 📋

My plan is to expand these topics but for now I am using the lists to keep track of the most initially useful and informative articles and documentation. I might remove some of these as I read them more closely and will definitely add others.

### Generative Engine Optimization

Spoiler: it’s basically good SEO.

- [Generative Engine Optimization: The new era of search](https://www.semrush.com/blog/generative-engine-optimization/): 
	- “[Microsoft’s official guidelines (PDF)](https://about.ads.microsoft.com/content/dam/sites/msa-about/global/common/content-lib/pdf/from-discovery-to-influence-a-guide-to-aeo-and-geo.pdf) for generative search reinforce this: make your catalogs machine-readable, structure content to answer real questions, and establish authority through credible sources and expertise signals. These are the same principles that drive traditional SEO success.”
- [Do AI models reward structured data? Testing schema in GEO](https://www.seerinteractive.com/work/case-studies/do-ai-models-reward-structured-data-testing-schema-in-geo): 
	- “Our theory [sic] was that LLMs recognize and reward structured data, especially when it highlights pricing information in a way that’s clear and intentional. By marking up specific pages with schema, we believed the content would become more trustworthy to AI models and more likely to be surfaced. As a result, we would be able to impact our client’s visibility among relevant queries in ChatGPT. 
	- **Validation:** After analyzing current AI bot behavior on our client’s site, we found that their top pagetype included AggregateOffer schema. The pages that contained this schema received 221% more GPT-related log hits than pages without.”
- [SEO for Google’s AI Overview](https://www.sistrix.com/ask-sistrix/ai-basics/seo-for-googles-overview-with-ai/)
- [What is Google AI Mode? (+ how to optimize for it in 2026)](https://www.semrush.com/blog/google-ai-mode/)
	- “Google AI Mode is built to understand natural, conversational queries similar to how people talk to voice assistants like ChatGPT or Google Assistant”
	- “Use question-based headings. Start with phrases like ‘How does…,’ ‘What is…,’ ‘Why does…,’ or ‘Can you…’ These match how users phrase queries.”
	- “Build out FAQ sections. Address common follow-up questions using a structured Q&A format. Add FAQ schema markup when possible.”
- [FAQ (FAQPage, Question, Answer) structured data](https://developers.google.com/search/docs/appearance/structured-data/faqpage)
	- Note that this is a new Schema.org type
	- Google says “FAQ rich results are only available for well-known, authoritative websites that are government-focused or health-focused.”

### Crawlers

Distinguishing LLM-related crawlers generally and understanding their subtypes.

- [AI and bot traffic trends (Nov 2025)](https://knownagents.com/posts/november-2025-trends-report)
- [Crawler list for AI user-agents (Dec 2025)](https://www.searchenginejournal.com/ai-crawler-user-agents-list/558130/)
- [List of AI/LLM user-agents](https://robotstxt.com/ai)
- [LLM-generated traffic in Adobe CJA](https://experienceleaguecommunities.adobe.com/adobe-analytics-3/tracking-and-analyzing-llm-and-ai-generated-traffic-in-adobe-customer-journey-analytics-12780) where it’s important to distinguish between:
	- Training crawlers
	- Agent crawlers
	- RAG crawlers
- [Overview of OpenAI Crawlers](https://developers.openai.com/api/docs/bots/) defines each of the three types for ChatGPT.
	- GPTBot → Training crawler
	- ChatGPT-User → Agent crawler
	- OAI-SearchBot → RAG crawler

### llms.txt

An interesting idea but highly speculative right now as to effectiveness.

- [Preparing your website for the future of AI search with llms.txt](https://www.1xinternet.com/en/highlights/llms-txt-website-visibility-ai-search)
- [The value of llms.txt: Hype or real?](https://www.mintlify.com/blog/the-value-of-llms-txt-hype-or-real)
- [What Is llms.txt and should you use it?](https://www.semrush.com/blog/llms-txt/)
- [Maryland’s llms txt file](https://www.maryland.gov/llms.txt)
- [AI basics: acronyms, meanings and reality](https://www.sistrix.com/ask-sistrix/ai-basics/)
- [llms.txt: How useful is the file for LLM optimisation?](https://www.sistrix.com/ask-sistrix/ai-basics/llms-txt-how-useful-is-the-file-for-llm-optimisation/)

## What can you measure? 📏

Making a change then observing differences in something measurable is the way to build a case that a particular technique is effective. This section will list scenarios that may be worth trying, including experiments reported by others. 

More to come…

**Important notes:** 

1.	Making an intervention and observing a change in a variable doesn’t mean the intervention caused the variable to change. The change might have happened anyway. Multiple experiments over time all supporting the same interpretation are needed to build confidence in a hypothesis. Where possible a control condition should exist where the intervention is not made.

2.	Supposing your intervention did cause the variable to change, that does not always support a causal explanation if the variable you are measuring is not the right one. To build support for causality one should also rule out alternative possibilities (sometimes called confounding factors) which are actually responsible for the observed change.

### Seer Interactive’s schema experiment

In [Do AI models reward structured data? Testing schema in GEO](https://www.seerinteractive.com/work/case-studies/do-ai-models-reward-structured-data-testing-schema-in-geo), Seer reports that when they *expanded* the structured pricing metadata using [AggregateOffer](https://schema.org/AggregateOffer) on a client’s key pages (i.e. they added more pricing details) they then observed a 12% increase in visits from ChatGPT’s Agent crawler `ChatGPT-User` and a 3% decrease in visits to the control pages. 

Seer interpreted this to mean that ChatGPT users were seeing their client’s experimental pages more because the `ChatGPT-User` hits were a reflection of what users were seeing real-time as answers to their questions within ChatGPT.

I think this is interesting though I want to know more about the assertion that the rate of hits from `ChatGPT-User` is a good (valid and reliable) proxy for users seeing the client’s content in ChatGPT.

## Best practices

 1. Use research and analytics to understand your users’ actual questions
 2. Organize and write well-structured content to address actual questions 
 3. Publish structured, semantic HTML content and avoid PDF, DOCX, TXT, etc.
 4. Avoid pages with thin content (< 200 words)
 5. Use headings for page structure (h2, h3, etc.) with appropriate nesting
 6. Use plain, conversational language where possible
 7. Ensure all content has a unique title and meta description
 8. Don’t rely on JavaScript to render content—it will be seen far less often
 9. Don’t hide content (e.g. using accordions or tabs)—it will be seen far less often
10. Add sufficient metadata fields to your CMS to support applicable schemas
11. Add applicable Schema.org metadata to your pages (as JSON-LD in `<head>`)
12. Don’t block crawl (see [Crawl control for websites](crawl-control-for-websites.md))
