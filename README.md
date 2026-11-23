# AWS Instance Price Suggester Chatbot

AI agent chatbot that recommends the best-value AWS EC2 instances from your memory, storage and use-case needs. It fetches and compares prices via async API calls, lets you pick one, collects region and security group config, then generates a ready-to-run CloudFormation YAML or AWS CLI script to launch it.

## Workflow

**Phase 1: Requirement gathering & pricing lookup**
User enters memory, storage and use case in the UI → AI agent calls the backend pricing APIs asynchronously → outputs are combined and compared → results are delivered to the user.

**Phase 2: Selection & deployment config**
User chooses one instance → AI agent prompts for security groups, AWS region and other configuration.

**Phase 3: IaC generation**
Backend validates the AMI and templates → generates a CloudFormation YAML file or AWS CLI script → AI agent formats the final output → user copies and runs it to spin up the EC2 instance.

## Project Structure

```
aws-instance-price-suggester/
├── backend/
│   ├── chatbot.py          # AI agent: requirements, selection, output formatting
│   ├── agent.py            # Agent logic and instance suggestion
│   ├── pricing.py          # Async AWS pricing lookup and comparison
│   ├── iac_generator.py    # CloudFormation / AWS CLI script generator
│   ├── main.py             # Python API entry point
│   ├── backend.js          # Node.js server
│   ├── package.json
│   └── requirements.txt
├── frontend/
│   ├── index.html          # Chat UI
│   ├── app.js              # UI logic and API calls
│   └── style.css
├── .env.example
├── .gitignore
└── README.md
```

## Tech Stack

- **AI Agent:** Python
- **Backend:** Python, Node.js
- **Frontend:** HTML, CSS, JavaScript
- **Cloud:** AWS Pricing API, EC2, CloudFormation, AWS CLI

## Setup

```bash
# Clone the repo
git clone https://github.com/ronitmaheshwari05/aws-instance-price-suggester.git
cd aws-instance-price-suggester

# Python backend
cd backend
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# Node server
npm install

# Environment variables
cp ../.env.example ../.env   # add your AWS credentials
```

## Roadmap

- [x] Project structure
- [ ] Requirement parsing with LLM
- [ ] Async pricing lookup and comparison
- [ ] Instance selection and deployment config
- [ ] AMI validation and IaC generation
- [ ] Chat UI

## Author

Ronit Maheshwari · [GitHub](https://github.com/ronitmaheshwari05) · [LinkedIn](https://linkedin.com/in/ronit-maheshwari-6b0363306)
