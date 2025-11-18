# PolicyPath

**The Auditable AI Orchestrator for Oncology Prior Authorization**

PolicyPath automates the end-to-end processing of oncology prior authorization requests, reducing approval times from days to minutes while ensuring full compliance, transparency, and auditability.

---

## 🎯 Problem Statement

Prior authorization (PA) for oncology treatments is a critical bottleneck in cancer care:
- Manual review takes **3-7 days** on average
- Delays access to life-saving treatments
- High administrative burden on payers and providers
- Prone to errors and inconsistencies
- Lacks transparency and auditability

---

## 💡 Solution

PolicyPath uses AI-powered workflow automation to:
- Extract clinical data from PDFs using OCR and NLP
- Validate insurance eligibility in real-time
- Apply payer-specific policy criteria automatically
- Route complex cases to human reviewers
- Generate comprehensive audit trails
- Export results to tracking systems

**Result:** Authorization decisions in **under 2 minutes** with full transparency.

---

## 🏗️ Architecture

PolicyPath is built on three core components:

### **1. Frontend (Loveable/React)**
- Patient data intake form with auto-fill
- Clinical PDF upload
- Real-time job status tracking
- Rich results display with audit trails
- Export functionality (PDF/JSON/Google Sheets)

### **2. Backend Orchestration (Opus)**
- Parallel data ingestion (Google Sheets + PDF OCR)
- AI-powered clinical data extraction
- Policy rule engine
- Decision logic with human-in-the-loop
- Comprehensive audit logging
- Google Sheets export integration

### **3. Data Layer**
- Google Sheets: Patient data and policy rules
- Supabase: Edge functions for API proxying
- Opus File Storage: Clinical PDFs and outputs

---

## 🚀 Features

### **Core Capabilities**
- ✅ AI-powered clinical data extraction from PDFs
- ✅ Automated policy rule matching (biomarkers, prior therapies, cost thresholds)
- ✅ Real-time insurance eligibility verification
- ✅ Human-in-the-loop review for complex cases
- ✅ Complete audit trail with timestamps and actions
- ✅ Export to Google Sheets for compliance tracking

### **Technical Highlights**
- **Parallel processing**: Simultaneous data ingestion from multiple sources
- **Normalization engine**: Unified data schema across sources
- **Performance metrics**: Sub-2-minute average processing time
- **Scalability**: Modular design supports multiple specialties and payers
- **Security**: PHI handling with secure file storage and API auth

---

## 🛠️ Tech Stack

| **Component** | **Technology** |
|---------------|----------------|
| **Frontend** | React, TypeScript, Tailwind CSS (Loveable) |
| **Backend** | Opus Workflow Automation |
| **Edge Functions** | Supabase (Deno/TypeScript) |
| **Data Storage** | Google Sheets API |
| **File Storage** | Opus S3-compatible storage |
| **AI/NLP** | Opus Native AI Agents (OCR, clinical extraction) |
| **Deployment** | Loveable (frontend), Opus Cloud (workflows) |

---

## 📦 Installation & Setup

### **Prerequisites**
- Opus account with API access
- Supabase project
- Google Sheets with PolicyPath Data structure
- Google Cloud project with Sheets API enabled

### **1. Clone Repository**
git clone https://github.com/yourusername/policypath.git
cd policypath


### **2. Frontend Setup**
cd frontend
npm install

Create `.env.local`:
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key


### **3. Supabase Edge Functions**
cd supabase/functions

Set secrets:
supabase secrets set OPUS_SERVICE_KEY=your_opus_key


Deploy functions:
supabase functions deploy opus-execute-job
supabase functions deploy opus-file-upload
supabase functions deploy opus-job-audit
supabase functions deploy opus-workflow-schema
supabase functions deploy opus-job-results


### **4. Opus Workflow**
1. Import workflow from `opus/workflow-export.json`
2. Configure Google Sheets connections
3. Update workflow input schema if needed
4. Test with sample data

### **5. Google Sheets Setup**
Create sheets in "PolicyPath Data":
- **Patient Demographics**: patient_id, name, dob, insurance_id, payer, etc.
- **Policy Rules**: payer, drug_name, required_prior_therapy, biomarker_requirement, etc.
- **PA Tracking Ledger**: Auto-populated by workflow with all results

---

## 🎮 Usage

### **Submit Authorization Request**
1. Navigate to dashboard → "Submit New Authorization Request"
2. Enter Patient ID (auto-fills demographics)
3. Upload Clinical Note PDF
4. Review auto-filled policy criteria
5. Click "Submit Authorization Request"

### **View Results**
- Real-time status updates
- Complete decision with rationale
- Failed criteria breakdown
- Human review details (if applicable)
- Audit timeline

### **Export**
- **JSON**: Complete structured output
- **PDF**: Formatted decision report
- **Google Sheets**: Auto-exported to PA Tracking Ledger

---

## 📊 Data Schema

### **Required Inputs**
{
patient_id: string,
name: string,
date_of_birth: date,
diagnosis_code: string,
planned_treatment: string,
insurance_id: string,
payer: string,
clinical_note_pdf: file,
// ... see full schema in docs/
}


### **Output Structure**
{
decision: "approve" | "deny" | "refer",
rationale: string,
criteria_failed: string[],
patient_info: { ... },
human_review_decision: { ... },
audit_log: { ... },
google_sheets_url: string
}


---

## 🧪 Testing

### **Run Frontend Tests**
npm test


### **Test Opus Workflow**
Use Opus UI to manually trigger with test data:
- Patient: PA001 (John Smith)
- PDF: Sample clinical note (provided in `test-data/`)

### **Sample Test Cases**
- ✅ **Approval**: PD-L1 ≥50%, prior therapy completed, active insurance
- ❌ **Denial**: Missing biomarker, inactive insurance
- 🔄 **Review**: Ambiguous prior therapy documentation

---

## 📈 Performance

| **Metric** | **Value** |
|------------|-----------|
| Average Processing Time | < 2 minutes |
| OCR Extraction Latency | ~90 seconds |
| Policy Evaluation | < 5 seconds |
| Success Rate | 98% (with valid inputs) |
| Throughput | ~30 cases/hour (single workflow) |

---

## 🔒 Security & Compliance

- **PHI Protection**: All patient data encrypted in transit and at rest
- **HIPAA Alignment**: Audit logs, access controls, data retention policies
- **Authentication**: Service key authentication for all API calls
- **File Security**: Presigned URLs with time-limited access

---

## 🛣️ Roadmap

### **Phase 1: MVP** ✅
- Core PA workflow automation
- Oncology specialization (NSCLC)
- Single payer (UnitedHealth)
- Manual form submission

### **Phase 2: Scale** 🚧
- Multi-specialty support (breast, prostate, colorectal cancers)
- Multi-payer policy libraries
- Batch processing
- Advanced analytics dashboard

### **Phase 3: Intelligence** 📅
- Predictive approval modeling
- Real-time policy updates
- Integration with EHR systems (HL7 FHIR)
- Appeal workflow automation

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details

---

## 👥 Team

Built during [Hackathon Name] by:
- Abhishekh Verma - Full-stack development, workflow automation
- Sivani Ajay - Data Analyst 
- Bhavya Sri Chinnamsetty - Frontend Development
- Vrushank Tipnis -  Frontend Development
- Kapish Roy - - Frontend Development

---

## 📞 Contact

- **Email**: abhishekh_verma2006@live.com
- **Demo**: [policypath.lovable.app](https://policypathai.lovable.app)

---

## 🙏 Acknowledgments

- **Opus** for workflow automation platform
- **Loveable** for rapid UI development
- **Supabase** for edge functions
- Healthcare professionals who provided domain expertise

---

**PolicyPath** - *Making cancer care faster, fairer, and fully traceable.*

---
