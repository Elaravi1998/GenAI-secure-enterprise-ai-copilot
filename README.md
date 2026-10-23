# 🛡️ Secure Enterprise AI Copilot

A starter GenAI portfolio project that answers questions from enterprise-style documents while applying basic role-based access-control checks, permission-aware retrieval, and audit metadata.

> **Security note:** This is an educational prototype, not a production security boundary. It uses synthetic sample documents and demo roles. Production systems require trusted identity integration, server-side authorization, secure storage, monitoring, and security testing.

## ✨ Features

- 🔐 **Role-based access control (RBAC):** Filter documents based on the user's demo role before retrieval.
- 🔎 **Permission-aware retrieval:** Rank only documents the role is authorized to access.
- 📚 **Source-grounded answers:** Return relevant authorized document excerpts and source identifiers.
- 🧾 **Audit metadata:** Record timestamps, role, source IDs, and query length without storing full prompt text by default.
- 🧪 **Security checks:** Test that restricted HR content is not retrieved for an employee role.
- 🧰 **Synthetic demo data:** Explore the workflow without connecting to private enterprise systems.
- 🛠️ **Extensible design:** Add an approved document store and an LLM response-generation layer.

## 🎯 Use Cases

- Internal policy and procedure assistants
- Employee self-service knowledge search
- Permission-aware enterprise document Q&A
- Secure knowledge retrieval prototypes
- Learning about authorization and auditability in GenAI applications

## 🧰 Tech Stack

- **Language:** Python
- **Notebook:** Jupyter / IPython
- **Retrieval:** TF-IDF and cosine similarity
- **Data handling:** Pandas
- **Sample data:** Synthetic enterprise policy documents

## 🏗️ How It Works

1. A user asks a question and selects a demo role.
2. The access-control layer filters documents by allowed role.
3. Retrieval ranks only the authorized documents.
4. The copilot returns relevant excerpts and source identifiers, or explains that no relevant authorized source was found.
5. Minimal audit metadata is recorded.
6. Basic tests check that restricted content stays out of results for unauthorized roles.

The current notebook uses a transparent retrieval prototype and does not yet call an LLM to generate answers. The demo role is supplied manually and must not be used as real authentication.

## 📁 Repository Structure

```text
secure-enterprise-ai-copilot/
├── secure_enterprise_ai_copilot.ipynb
├── README.md
└── requirements.txt
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/secure-enterprise-ai-copilot.git
cd secure-enterprise-ai-copilot
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Create a virtual environment

**Windows PowerShell:**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install pandas scikit-learn jupyter
```

### 4. Run the notebook

```bash
jupyter notebook
```

Open `secure_enterprise_ai_copilot.ipynb` and run the cells from top to bottom.

## 🧪 Example

The notebook includes synthetic documents for annual leave, password and MFA guidance, expense reimbursement, incident response, and confidential compensation guidance.

Try asking about annual leave as an `employee`, then search for compensation planning records. The employee role should not retrieve the HR-only compensation document.

## 🔐 Security Considerations

- Never trust a role supplied directly by a user in a production system.
- Authenticate users with a trusted identity provider and enforce permissions on the server.
- Apply document-level permissions before retrieval and before tool execution.
- Treat retrieved documents as untrusted input and defend against prompt injection.
- Avoid logging sensitive prompts or full responses unless there is a justified, protected audit requirement.
- Store credentials in a secrets manager and restrict access to logs.
- Test for cross-user data leakage, permission bypass, and prompt injection.
- Review model-provider data retention and processing terms before sharing enterprise content.

## 🗺️ Roadmap

- [ ] Connect to an approved enterprise document store
- [ ] Add an LLM response-generation layer with citations
- [ ] Replace demo roles with trusted identity-provider claims
- [ ] Add permission-aware chunking and retrieval
- [ ] Build a Streamlit interface
- [ ] Add adversarial security and regression tests

## 🤝 Contributing

Suggestions and improvements are welcome. Open an issue to discuss a feature or submit a pull request with a clear description.

## 📄 License

Choose a license and add the corresponding `LICENSE` file before publishing. Do not claim a license until that file has been added.
