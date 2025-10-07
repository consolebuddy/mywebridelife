flowchart TD
  A[IntakeAgent] --> B[DocParse & Struct]
  B --> C[NoticeClassifier]
  C -->|ASMT-10| D[EvidenceCollector]
  C -->|DRC-01/07| D
  C -->|GSTR-3B v 2A/2B| D
  D --> E[IssueDecomposer]
  E --> F[RAG Retriever + PolicyCiter]
  F --> G[DraftWriter]
  G --> H[FactChecker & CoverageMeter]
  H -->|low risk| I[Formatter & Annexures]
  H -->|high/med risk| J[[Interrupt: LegalReview]]
  J -->|approve| I
  J -->|changes| G
  I --> K[Export Packager (PDF/Docx/Zip)]
  K --> L[Write Audit Log]
