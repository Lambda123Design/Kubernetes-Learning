# Kubernetes-Learning

1. Waterfall Model

Era: 1970s–1990s (first formalized by Winston Royce in 1970)

Concept

Linear and sequential approach.

Each phase must be completed before moving to the next.

No overlapping or going back.

Phases

Requirement Analysis → Collect and document all requirements.

System Design → Architecture, database design, interface design.

Implementation (Coding) → Developers write the code.

Testing → QA team tests the system after coding is done.

Deployment → Deliver software to customer.

Maintenance → Fix bugs, provide updates.

Strengths

✅ Easy to manage (clear structure).
✅ Good for projects with fixed, well-understood requirements (e.g., government, defense, manufacturing).
✅ Strong documentation.

Weaknesses

❌ Very rigid — changes are difficult once development starts.
❌ Testing happens late → bugs are found too late.
❌ Long delivery cycle — no working software until the very end.

👉 Best for: Construction, aerospace, regulated industries.

🔹 2. Agile Model

Era: 2001 onwards (Agile Manifesto)

Concept

Iterative and incremental approach.

Focus on delivering small, working software quickly and improving it with continuous feedback.

Values: Individuals & interactions > Processes & tools.

Phases (iterative cycles called Sprints in Scrum)

Requirement/User Stories → High-level requirements written as stories.

Planning & Design → Decide what goes into the sprint.

Development → Build features in small increments.

Testing → Continuous testing alongside coding.

Review & Feedback → Show working software to customer.

Retrospective → Improve process in next sprint.

Strengths

✅ Highly flexible, adapts to changes.
✅ Delivers working software quickly (early value to customer).
✅ Continuous customer feedback → high satisfaction.
✅ Team collaboration and ownership.

Weaknesses

❌ Hard to scale in very large projects without frameworks (SAFe, LeSS).
❌ Documentation sometimes neglected.
❌ Requires skilled, self-organizing teams.

👉 Best for: Startups, dynamic projects, fast-changing business needs.

🔹 3. DevOps

Era: 2010 onwards (extension of Agile + CI/CD culture)

Concept

Integrates Development + Operations into one continuous process.

Goal: Faster delivery, automation, reliability, and collaboration.

Extends Agile by automating delivery pipelines.

Key Practices

Continuous Integration (CI) → Developers merge code frequently; automated builds/test run.

Continuous Delivery/Deployment (CD) → Code automatically deployed to staging/production.

Infrastructure as Code (IaC) → Infrastructure managed by code (Terraform, Ansible).

Monitoring & Logging → Continuous feedback from production.

Automation → Testing, deployment, infrastructure provisioning automated.

Strengths

✅ Faster release cycles.
✅ Higher quality through automation.
✅ Collaboration between Dev, QA, and Ops.
✅ Scalability (cloud-native + containers).

Weaknesses

❌ Requires cultural change (Dev & Ops teams must work together).
❌ Tooling can be complex (Jenkins, Docker, Kubernetes, GitHub Actions, etc.).
❌ Security concerns if CI/CD not managed properly → led to DevSecOps.

👉 Best for: Cloud-based applications, large enterprises, continuous delivery needs.

📊 Comparison: Waterfall vs Agile vs DevOps
Aspect	Waterfall 🪜	Agile 🔄	DevOps ⚡
Process	Sequential	Iterative	Continuous
Delivery	At the end	In small sprints	Continuous (CI/CD)
Flexibility	Very low	High	Very high
Customer Involvement	Low	High	High
Testing	After coding	Parallel to coding	Automated & continuous
Speed	Slow	Faster	Fastest
Best for	Fixed, stable projects	Changing requirements	Cloud, automation, frequent releases

👉 You can think of them as:

Waterfall → "Plan everything first, then build once."

Agile → "Build small pieces, get feedback, improve continuously."

🔹 Kubernetes Components
1. Control Plane Components (manage the cluster, make global decisions)

API Server (kube-apiserver)

Entry point of the cluster.

All components, CLI (kubectl), and users talk to it via REST API.

Handles authentication, validation, and communication.

etcd

Key-value database that stores the cluster state (pods, services, configs, etc.).

Highly available and consistent.

Controller Manager (kube-controller-manager)

Runs controllers that ensure the cluster state matches the desired state.

Examples:

Node Controller → tracks node health.

Replication Controller → ensures correct number of pods.

Endpoint Controller → updates Services.

Scheduler (kube-scheduler)

Assigns newly created pods to nodes.

Decides placement based on resources, constraints, taints/tolerations, affinity, etc.

2. Node Components (run on every worker node)

Kubelet

Agent on each node.

Talks to API Server.

Ensures containers are running as defined in PodSpecs.

Kube-Proxy

Handles networking on each node.

Manages Services, load-balancing, and forwarding traffic to pods.

Container Runtime

Runs containers.

Examples: containerd, CRI-O, Docker (deprecated).

3. Add-on Components (not core, but essential in real use)

DNS (CoreDNS)

Provides internal DNS for Services and Pods.

Lets pods talk to each other with names instead of IPs.

Ingress Controller

Manages external access (HTTP/HTTPS) to services.

Example: NGINX Ingress, Traefik.

Dashboard

Web UI for managing the cluster.

Monitoring & Logging

Tools like Prometheus, Grafana, Fluentd, ELK stack.

Network Plugins (CNI)

Provide pod-to-pod networking across nodes.

Examples: Calico, Flannel, Cilium, Weave.

📊 Summary: Kubernetes Components
Control Plane

API Server

etcd

Controller Manager

Scheduler

Node

Kubelet

Kube-Proxy

Container Runtime

Add-ons

CoreDNS

Ingress Controller

Dashboard

Monitoring & Logging

Network Plugins

DevOps → "Automate everything, deliver continuously, monitor in real-time."
