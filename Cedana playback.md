

**CEDANA: BUSINESS BRIEF**  
 

**CONTEXT — THE AI INFRASTRUCTURE CHALLENGE**

AI is no longer just a software story. As companies build and deploy AI at scale, the underlying compute infrastructure — specifically GPUs (Graphics Processing Units, the specialised chips that power AI workloads) — has become the single most critical and expensive input into any AI product or service.

Understanding how AI computation works at a basic level is important context:

•      When a user submits a query to an AI model (e.g. "write me a summary of this document"), the processing happens in two stages:

–     Pre-fill: the system analyses every token (word/piece of text) in the query against every other token to understand the full context

–     Decode: the system generates the response, token by token, translating the result back into readable text

•      These two stages run continuously together — prefill, decode, prefill, decode — to serve each user request

The critical difference between traditional computing (CPU-based) and AI computing (GPU-based):

•      Traditional CPU workloads are inherently "stateless" — all progress is saved to databases. If a CPU cluster fails, computation can restart from the last saved checkpoint immediately from the database, with little or no lost work

•      GPU workloads for AI are fundamentally different — they combine execution and data into one massive, in-memory workload. Unlike CPUs, GPUs do not rely on databases for their in-flight state. If a GPU workload fails or is interrupted, all in-progress computation is lost and must be restarted from scratch

•      As AI is used for increasingly complex tasks — long document analysis, multi-step agentic workflows, advanced coding — GPU workloads are becoming "stateful": they build up rich in-progress state over minutes, hours or days, making any interruption extremely costly

The scale and cost of this problem:

•      GPUs cost $3–4 per hour per unit, and modern AI workloads can run on 1, 4, 8, 16 or more GPUs simultaneously

•      A critical internal statistic cited by a leading university data centre: up to 65% of all GPU compute time is wasted on re-computation due to failures, cancellations and restarts

•      Nvidia's flagship H100 GPU has an 8–9% annual hardware failure rate; after 3 years, 20–30% of a fleet may have burned out

•      Inference — serving AI responses to real users — is the fastest-growing GPU workload. Three years ago, the training-to-inference ratio for GPU usage was approximately 80:20. It is already 60:40 and projected to reach 20:80 by 2030

 

**CATEGORY**

The category Cedana operates in does not yet have a settled, universal name. Terms in use include:

•      GPU Checkpointing and Orchestration — the most technically precise description

•      Workload Preemption — the ability to pause, save and resume GPU workloads on demand

•      Compute Shaping — Cedana's own coined term: "the ability to shape computing dynamically in real time, the way we deal with energy"

•      The closest recognised analogy is VMware's vMotion — a feature that allowed live migration of entire virtual machines between physical servers with zero downtime. When Cedana describes itself to data centre audiences, the response is often: "you are vMotion for GPUs"

The category is extremely nascent. There is no established incumbent. Most organisations are simply living with the GPU reliability and utilisation problem, often unaware that a solution is technically possible.

Key category tensions that define the buying problem:

•      SLAs vs. Overprovisioning: To serve user queries with low latency, inference companies must keep "warm replicas" running at all times — essentially spare GPU workloads sitting idle so they are instantly ready when demand spikes. Because starting a new GPU workload from scratch takes 5–15 minutes, companies must overprovision by 20–80% above their average load. This idle GPU spend is enormous

•      Cost vs. Reliability: When a GPU fails or maintenance is required, all in-flight work is lost. The longer the job, the greater the loss. A week-long training job interrupted on day 6 restarts at day 0

•      Security vs. Uptime: GPU software must be patched regularly for security vulnerabilities. Doing so requires shutting down GPU workloads — forcing organisations to choose between security risk and operational disruption

•      Utilisation vs. Flexibility: Enterprise GPU clusters are shared across many internal users, who systematically overestimate how many GPUs they need. The result is significant idle GPU capacity sitting unused while other users queue for access

 

**COMPETITIVE PLAYERS**

There is no established incumbent in this category. Most customers are simply unaware that the GPU checkpointing problem can be solved at a system level. The competitive landscape is thin:

**Application-Level Checkpointing (manual, by the customer)**

•      The default approach today. Developers write custom code to save their own workload state to storage, and reload it if the job fails

•      Significant developer overhead. Only works for training workloads — not possible for inference

•      PyTorch (the most popular AI framework) has a built-in application checkpointing feature, but it requires integration effort and management

**Loophole Labs**

•      Uses a checkpoint driver that Nvidia released

•      Not reliable enough and insufficient coverage for production workloads

**Clockwork**

•      Recently started doing training checkpointing

•      Claims transparency but provides an application-level framework, not system-level checkpointing

•      Cedana's assessment: their system-level checkpointing does not work

**CRIU (Open Source)**

•      An open-source solution for CPU checkpointing only

•      Cedana actually uses CRIU as a component of its own solution — because CPUs act as host controllers for GPUs, CPU state must also be captured

**"Company X" (unnamed)**

•      Copied Cedana's website animations. Focused on CPU migration, not GPU migration

**Build vs. Buy (most significant competitive dynamic)**

•      The most common alternative is for organisations to build their own workload management and checkpointing tooling in-house

•      This is a significant engineering investment. Cedana's advantage is that it is out-of-the-box, protocol-agnostic and continuously updated as Nvidia and the wider ecosystem evolve

Cedana's assessment of its competitive position was validated by a key third party: Cambridge University evaluated all available options and concluded Cedana was the only team solving this at the system level.

 

**CUSTOMER AND SEGMENTS**

Cedana has identified two primary customer segments at this stage of the company:

 

|   | ENTERPRISE AI ORGANISATIONS | INFERENCE AT SCALE COMPANIES |
| :---- | :---- | :---- |
| **Who they are** | Pharma, finance (quant funds), research institutions, supercomputing labs, universities | Companies running AI models as a production service — serving inference to real users or downstream applications. Examples: Together AI, Baseten, CoreWeave, Nebius, Hyperbolic, Cerebrium |
| **GPU scale** | 300 to 10,000+ GPUs. Often shared clusters across multiple internal user groups | Large inference fleets. Together AI is \~$1bn ARR. These companies measure cost in GPU-hours |
| **Primary pain** | Wasted compute from failures and restarts (up to 65% of compute time) Poor GPU utilisation (30–40% effective utilisation on many shared clusters) Maintenance windows that kill long-running experiments or jobs Poor resource sharing between competing user groups — overallocation, priority conflicts | Overprovisioning: must keep 20–80% spare "warm replica" workloads running at all times to serve latency SLAs Cold start latency: 5–15 minutes to bring a new inference workload online Model-dependent unpredictability: cold start time varies enormously by model size, making autoscaling unreliable |
| **Workload types** | Training, fine-tuning, batch inference, scientific compute (protein folding, computational fluid dynamics, financial algorithms). Job durations: hours to weeks | Online inference (real-time, user-facing) and batch inference. Stateful workloads increasingly common as context windows grow (50k–150k+ tokens per session) |
| **Decision maker** | Director of HPC, VP Infrastructure, CTO. Sysadmin/Linux admin are key influencers | CTO, VP Engineering, Head of Infrastructure |
| **Pricing model** | Annual contracts: $76k–$300k (approx. $100k per 100 GPUs, scaling upward) | Per memory/GPU/month pricing (e.g. $2/GPU/month, discounted to $1 at scale). Margins close to 90% |
| **Current examples** | Abbvie, Harvard, G Research, MSI (Minnesota Supercomputing Institute), KSU, QRT | Together AI (most advanced engagement), Baseten. CoreWeave, Nebius, Hyperbolic as targets |

 

**Additional sub-segments within Enterprise AI**

•      Academic/Research institutions (R1/R2): High research focus (Stanford, MIT type). Purchase behavior is unique — procurement processes, security clearances, different sharing models

•      National Labs (e.g. DOE/NERSC/Lawrence Livermore): Government procurement processes are very different; security requirements are stricter

•      Supercomputing centres: Institutions like Ohio State's supercomputing centre that serve multiple universities — and sometimes resell spare compute capacity. Spot instances are highly relevant here

•      Finance — quant funds: Immediately understand the value of compute efficiency. Own proprietary financial algorithms with strict confidentiality requirements. Regulatory continuity requirements (DORA, OSFI) are an additional buying driver

•      Pharma: Use workloads like AlphaFold (protein folding simulation), Gromacs (DNA computation), computational chemistry. Regulatory continuity is a growing angle

•      Emerging enterprise segment: Fortune 100/500 companies (e.g. Abbvie, AstraZeneca) that have started buying GPUs in the last 24 months. New buyer profiles — VP/Head of AI/ML — who are newer to GPU infrastructure decisions

 

**KEY BUYING SIGNALS**

Organisation signals

•      Organisations running shared GPU clusters with multiple internal user groups — universities, research institutions, enterprises with AI CoEs

•      Companies or institutions that have purchased Nvidia DGX systems, H100 clusters or reserved GPU instances in the last 24 months

•      Infrastructure or HPC team with 10+ years of experience — these people understand "checkpointing" immediately and don't need it explained

•      Job postings for VP of AI/ML Infrastructure, Director of HPC, Head of GPU Infrastructure

•      Inference companies with significant SLA commitments and large model deployments (running 200–400bn parameter open-source models that require 8–16 GPUs per workload)

Behaviour signals

•      Public discussions about GPU failure rates, recompute overhead, maintenance window pain — on message boards for services like Cursor, agentic platforms, or HPC user forums

•      Companies running their own open-source models (vs. using OpenAI/Claude APIs) — these are the ones where Cedana can help; when others use a frontier lab's compute, Cedana cannot intervene

•      Finance and healthcare organisations where regulatory continuity (DORA, OSFI compliance) requires provable recovery and audit trails for AI workloads

•      Organisations running long-context inference workloads (50k–150k+ token context windows) — these are most exposed to the cold start and reliability problems

 

**INTRODUCTION TO CEDANA**

•      Cedana was founded by a team with backgrounds in AI healthcare and robotics — fields where system failure has immediate, high-stakes consequences

•      The healthcare co-founder built and sold an AI healthcare company. His framing of reliability: "if anything goes wrong, 50,000 patients get a phone call"

•      The robotics co-founder had first-hand experience of what happens when a GPU workload fails: "a failure meant the robot was a brick for an hour"

•      The founding insight was directional: while most AI companies were moving up the stack (building applications, interfaces, "vibecoding"), Cedana saw more value in going deeper into the infrastructure layer

•      The broader vision: "if you can make compute more liquid — not only your workloads but other workloads on your system to other clusters, other zones — you can start to have compute shape to demand in real time. You can move compute like a commodity — where it is cheaper, where it is higher performance, lower latency. Move compute like electricity"

•      The team spoke to 120 people to understand the market and the problem before building. Some of those conversations became customers; others became investors

•      The company was accepted into Y Combinator and backed by Pebblebed (an OpenAI investor)

•      A particularly important validator: Keith Adams — an early member of VMware's VM virtualisation team — became an investor after understanding what Cedana was building. VMware's vMotion (live migration of virtual machines) is the closest analogy to what Cedana does for GPUs

•      The technology took three years to get right. An early POC with Samsung proved difficult — Samsung's workloads were highly customised — but gave the team invaluable coverage across workload types. The team now supports single-node, multi-GPU, multiple inference engines (vLLM, SGLang, Triton) and a full registry of CUDA test cases

 

**PRODUCT**

Core Technology: GPU Checkpointing and Migration

A "checkpoint" is a complete snapshot of a GPU workload's entire state at a point in time — GPU memory state, computation state, networking state, file system state, CPU state — captured and saved to storage so the workload can be resumed exactly where it left off, on the same or a different GPU.

The critical and distinctive thing about Cedana's checkpointing is where it operates: at the OS and kernel level, not the application level. This means:

•      No code changes required from the end user or their developers

•      Completely transparent — the user or researcher often doesn't know Cedana is running

•      Works for inference workloads, not just training — something no application-level checkpoint can do

•      In Kubernetes environments, a user simply adds a single line (.classCedana) to their configuration

•      In Slurm environments (the standard job scheduler for HPC/research), there are no commands to learn or change — the job simply reappears in the queue with the same job number after an interruption

Architecture: Cedana sits between the OS and container runtime in the GPU infrastructure stack — GPU infrastructure → OS → Cedana → Container runtime → Kubernetes → Frameworks (PyTorch etc.) → User workloads. This positioning gives Cedana full visibility and control without requiring any changes to the layers above or below it.

Three levels of GPU checkpoint coverage

•      Single GPU: fully supported

•      Multi-GPU (4/8/16 GPUs on the same physical board, coordinating via NVLink): fully supported — Cedana coordinates the checkpoint across all GPUs simultaneously

•      Multi-node (multiple boards connected across a cluster): in active development. This is where the largest training workloads live, and Cedana is close to solving it

**The Five Core Use Cases**

**1\. Maintenance Windows ("Stop and Start")**

Problem: GPU security patches, version upgrades and hardware repairs require shutting down GPU workloads. Any work in flight is lost and must restart from scratch. A week-long training job interrupted at day 6 restarts from day 0\. CoreWeave faced this directly: a zero-day security vulnerability required patching 50,000 GPUs — the cost of stopping all in-flight training jobs ran to millions of dollars.

Cedana solution: continuously checkpoints all running workloads (every 60–90 seconds, depending on workload size). When maintenance happens at midnight, the maximum loss is one minute of computation. Workloads automatically resume exactly where they left off when GPUs come back online. Completely transparent to both admins and end users.

*"We take snapshots continuously — every minute, minute and a half depending on the size of the workload"*

**2\. Warm Replicas and Cold Start Reduction**

Problem: Inference companies need to respond to user queries in seconds. But bringing a new GPU inference workload online from cold (loading a massive AI model into GPU memory) takes 5–15 minutes. To maintain low latency, companies must "overprovision" — keep 20–80% more inference workloads running at all times than they actually need, just in case traffic spikes. This idle GPU cost is enormous and directly affects margins.

An additional complexity: cold start time today depends on model size — a 7-billion parameter model cold starts faster than a 100 or 405-billion parameter model. This unpredictability makes autoscaling hard to engineer reliably.

Cedana solution: reduces cold start from 5–15 minutes to 30–90 seconds (2–10x improvement). Critically, Cedana's cold start time is decoupled from model parameter count and instead determined by GPU VRAM (memory) — making it predictable: "If a GPU has 80GB RAM, we'll tell you it's 25–35 seconds. If it's an 8x GPU with a 405B model, 70–80 seconds." This predictability enables proper autoscaling algorithm design.

This also enables a finer-grained approach to overprovisioning — different model sizes need different overprovisioning buffers, and Cedana's predictable cold starts allow admins to set these correctly.

**3\. Hardware Failure and Disaster Recovery**

Problem: H100 GPUs have an 8–9% annual failure rate. After three years, 20–30% of a fleet may have burned out. For inference workloads running on 8 or 16 GPUs, a single GPU failure takes down the entire distributed workload ("blast radius"). For workloads serving 50,000 concurrent user sessions, that is a significant reliability event.

Cedana solution: when a GPU burns out, Cedana automatically resumes the workload on a replacement GPU. With continuous checkpointing, the maximum loss is under one minute of work.

**4\. Workload Preemption and Resource Sharing ("Liquidity")**

Problem: In shared GPU clusters — universities, enterprise AI teams, supercomputing centres — different user groups compete for the same GPU resources. Users systematically overestimate how many GPUs they need (asking for more to avoid being bottlenecked). When a high-priority job arrives, the admin must kill lower-priority jobs to free up resources — destroying all their in-flight work. This is politically charged and operationally painful. In some naval research labs, three departments share three clusters funded separately — and want to offer spare capacity to each other, but cannot without the risk of disrupting each other's work.

Cedana solution: enables safe preemption — save the lower-priority job to storage, run the high-priority job, then seamlessly resume the lower-priority job on the next available GPU with no work lost. Also enables dynamic resizing of overallocated jobs (detecting by the hour where users have claimed more GPUs than their actual workload uses).

*"We create a queue that intelligently looks for GPUs that are free. And when you get kicked off, all you have to do is requeue and you'll be on the next available GPU without loss of work"*

**5\. Spot Instances (GPU Marketplaces)**

Problem: Organisations with spare GPU capacity (created by better utilisation from Cedana) can, in principle, offer discounted capacity to lower-priority users. But doing so is risky — when the primary workload needs its GPUs back, the spot user loses all their work.

Cedana solution: spot users' workloads are automatically checkpointed and requeued when preempted, with no work lost. This makes GPU spot markets practically viable.

**Integrations and Ecosystem**

•      Nvidia Dynamo: the gold standard for AI inference performance. Cedana has integrated with Dynamo and validated results — 9.6x faster cold start, cold start independent of model size, native support for disaggregated serving (Nvidia's approach to separating prefill and decode workers for higher GPU performance). Cedana has validated this with major inferencing companies

•      Slurm: the standard job scheduler for HPC and research institutions. Cedana commands Slurm — after a job is preempted and resumed, the researcher sees their old job number reappear in the queue as if nothing happened

•      Kubernetes: single-line integration (.classCedana)

•      Inferencing engines: vLLM, SGLang, Triton (3–4 of the major inferencing engines)

**Key Metrics Cedana Tracks and Markets**

•      Time to First Token (TTFT): how quickly an inference workload can serve a first response to a user. Cedana's faster cold starts directly reduce TTFT by 2–10x

•      Time Between Tokens: this metric should be unchanged by Cedana — used to demonstrate seamlessness

•      Cold Start Latency: milliseconds. Cedana is integrating with the Minnesota Supercomputing Institute to get their database of jobs submitted, retried and failed — to generate a real, peer-reviewed marketing number for wasted compute time

•      GPU Utilisation: Cedana takes organisations from 30–40% effective utilisation to 70–80%+

•      Effective Throughput (vs. raw throughput): an important insight — organisations talk about "GPU utilisation" and "throughput" but do not account for all the compute lost to failures and restarts. Cedana's UI can show how many times a job actually failed and restarted, revealing the true effective throughput

 

**INPUTS TO POSITIONING / VISION / PURPOSE**

*"We are the VMware for AI. VMware's whole thing was they could take a single machine and virtualise it — you could run two different operating systems on it. Datacentres used it because you could move your entire VM from one machine to another. People go: oh, you are vMotion for GPUs"*

*"Compute shaping — the ability to shape computing dynamically in real time, the way we deal with energy. You can start taking advantage of that arbitrage: move compute like electricity, like Abu Dhabi is doing"*

*"If you can make compute more liquid — not only your workloads but other workloads on your system to other clusters, other zones — you can start to have compute shape to demand in real time. Move compute like a commodity — where it is cheaper, where it is higher performance, lower latency"*

*"We are arbitraging storage costs for compute costs — use cheap storage to manage your compute"*

*"Inference is going to be the largest workload of our lifetime. We're helping people get more work done"*

*"User doesn't even need to know Cedana exists. Seamless and transparent — we are completely seamless and transparent"*

*"We felt it would be valuable for us to go deeper into the system. Everyone was going up the stack. We went the other way"*

*"We are the only ones — or the only idiots — working on this for a long time"*

*"Portable AI workloads is a moving frontier. The resume problem expands from process state to co-ordinated system state"*

*"Utilisation is a fraud if you measure it wrong. You can be running a job at 90% utilisation — but if it failed and you kept restarting, the effective value is much lesser. You should really measure how much effective work you are doing"*

 

**SALES AND MARKETING**

Current Status

•      Pre-revenue. Minnesota Supercomputing Institute: $100k deal awaiting final agreement. Two additional POCs signed

•      Abbvie: "we want to use you, but it's a matter of timing"

•      Ratio of outbound approach to meeting booked: approximately 1:10

•      Primary GTM channels to date: personal networks, Y Combinator network, investor introductions, conference attendance

Key Strategic GTM Moments

•      AWS reached out to Cedana and invited them to present to 40+ AWS Solution Architects. This gives Cedana access to AWS customers buying GPUs and running their own inference workloads — AWS is trying to make its GPU offering stickier vs. "neo cloud" GPU providers (which offer cheaper raw GPU pricing). Cedana increases the effective value of AWS GPU purchases

•      Nvidia Dynamo integration: this creates a clearly marketable product form factor — "Cedana-powered Dynamo" — that is a narrow but sharp wedge into the inference-at-scale segment. The validated benchmark results (9.6x cold start improvement) are a strong proof point

•      Cambridge partnership: Cambridge evaluated all available competitors and endorsed Cedana as the only team solving GPU checkpointing at the system level. Their quote: "Word spreads fast"

**Sales Stories**

**Together AI**

Together AI is one of the leading independent inference platforms (\~$1bn ARR). Even their CTO — who "breathes inference" — took time to fully understand what Cedana was doing at the OS level. Cedana sent results from a POC, and he called back within 3 minutes. Together has been working with Nvidia on inference performance and rates Cedana's approach as superior. "Do I need to do anything with my inferencing engine?" — No.

**Abbvie**

The pharma enterprise segment. Admins are excited specifically about the maintenance window use case — it directly removes the most painful recurring operational problem. Commercial timing is the remaining hurdle.

**Harvard (FAS and Kempner Institute)**

Testing Cedana for coverage across physics, math, simulation workloads; endurance and scale; CPU and GPU workloads. A rigorous validation process. Harvard also gave Cedana a key rejection reason to solve for: access permissions ("we can't give you root permission" — since solved).

**G Research**

Quant hedge fund. Immediately understood the value of workload reliability and compute efficiency. The "memory under management" framing resonated: they think naturally in terms of assets under management and computing resources as similar asset classes.

**Supercomputing 2026 (Target)**

The major annual HPC conference. The goal is to arrive with 2–3 strong published case studies and use the event as a major conversion moment. One prior conference appearance generated significant interest from the audience.

**Sales Approach by Segment**

•      For HPC / research institutions: the word "checkpoint" is immediately understood. The key selling point to explain is transparency — that Cedana works at the OS level without any changes to researcher workflows. The magic moment: showing Slurm commands working as if Cedana doesn't exist, with a failed long-running job silently resumed

•      For inference at scale: the Dynamo integration is the wedge. Validated benchmarks on cold start latency are the proof point. The conversation quickly moves to overprovisioning economics

•      For enterprise AI organisations: the maintenance window use case is the most immediately relatable pain — admins hate the forced choice between security posture and losing in-flight work

**Demo Experience**

The demo reliably turns conversations. The key moment is showing stateful reliability — a new container automatically reloaded with the workload exactly where it left off. The typical response: "This is something we haven't seen before." For Slurm users, it's hearing that their standard commands work unchanged — Cedana is entirely invisible. This is consistently described as the turning point in technical evaluations.

Deck Structures

•      Enterprise AI / Research institutions deck: cost of wasted compute (cluster of H100s at 30–40% utilisation \= $1–2mn+ wasted annually), automated checkpointing and migration solution, ROI: 40% utilisation improvement, 2x throughput increase, fewer failed jobs and support tickets, maintenance windows solved

•      Inference at scale deck: AI is now an operating cost / inference dominates AI operating costs; portable AI workloads as a moving frontier; Dynamo integration; cold start benchmark results; overprovisioning reduction economics

Marketing Ideas and Observations

•      A clear content stream around the Dynamo integration: signals to Nvidia that Cedana is a serious ecosystem partner and creates a marketable product form factor

•      2–3 strong published case studies: the HPC community moves on reputation and peer validation — "word spreads fast"

•      HPC user forums (e.g. Hyperion Research) as a targeting and content channel

•      Supercomputing 2026 conference as a major GTM milestone

•      The "effective throughput" framing (vs. raw GPU utilisation) as a thought leadership angle — surfacing a metric that most organisations are not currently tracking

•      AWS partnership: the 40+ solution architect contacts represent a targeted list of organisations actively buying and deploying AWS GPU infrastructure

 

On the marketing aspiration — companies admired for their go-to-market:

•      Vercel: "did a really good job, beat others at their marketing"

•      Databricks: strong technical thought leadership

•      Temporal: "a good example — a smaller company nailing AI"

**WHAT KEEPS THE FOUNDERS AWAKE AT NIGHT**

Short term

•      Demand generation consistency: the approach-to-meeting ratio is 1:10 and follow-up consistency has been an issue. The goal is a repeatable pipeline

•      "In the next 6 months we should show it's the right choice to make" — proving commercial traction alongside technical proof

•      Closing the Minnesota deal and converting the two active POCs to revenue

•      Messaging and positioning: "with marketing I want a certain number of KPIs in my CRM — calls booked, a close process that's validated". Finding the unifying message that works across both the enterprise and inference segments: "if we can come up with a single architecture that's valid for both enterprise and inference companies…"

Medium term

•      Multi-node checkpointing: the ability to checkpoint workloads running across 100–1,000 GPUs on multiple connected boards. This is where the largest training workloads live. It is in active development but "not an immediate focus anytime soon"

•      Finance and healthcare expansion: a new investor is specifically focused on healthcare and finance, opening up the regulatory continuity angle (DORA, OSFI) and the pharma computational workload angle. Targets include Barclays and JP Morgan trading houses

•      Building 2–3 high-quality case studies: the Cambridge endorsement is that "word spreads fast" in this community — case studies are the unlock

Long term

•      Expanding from the enterprise AI / HPC segment into the inference-at-scale segment (Together AI, Baseten, CoreWeave). Thesis: inference will be the dominant AI workload by 2030 (20:80 training-to-inference ratio), and stateful inference is a fast-growing problem as context windows and agent workflows grow longer

•      The larger vision: "compute shaping" — making GPU compute as liquid, elastic and efficiently allocated as electrical power on a grid. The ability to move AI workloads across clusters, availability zones, cloud providers and on-prem infrastructure in real time based on cost and performance

•      The category is nascent and wide open: "inference is going to be the largest workload of our lifetime"

 

