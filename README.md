# llsm-assignment
# Republic of Moldova — IMF Report Analysis Using LLMs

*Student reference number:* 24076688  
*Source document:* Republic of Moldova: 2025 Article IV Consultation, IMF Country Report No. 26/59 (2026)  
*Environment:* Google Colab (Python)  
*Notebook:* Moldova_IMF_14_Cells_With_Outputs.ipynb

## Overview

This notebook analyses a 100-page IMF country report using a lightweight large language model (LLM), structured information extraction, local semantic retrieval and financial visualisation. It covers all four assignment tasks and includes a comparison of single-query and multi-query Retrieval-Augmented Generation (RAG).

The implementation uses *Gemini 3.5 Flash-Lite* for text generation and evaluation, *PyMuPDF* for PDF extraction, *Sentence Transformers* for local embeddings, *FAISS* for retrieval, and *Pandas/Matplotlib* for analysis and visualisation.

## Files needed

- Moldova_IMF_14_Cells_With_Outputs.ipynb — the 14-cell executable notebook.
- MOLDOVA.pdf — the source IMF report. The filename is case-sensitive.
- README.md — these instructions.

The report PDF is an input and must be present in the Colab runtime; saved notebook output cells do not replace the PDF or the API configuration.

## Running the notebook in Google Colab

1. Open Moldova_IMF_14_Cells_With_Outputs.ipynb in *Google Colab*.
2. Upload the IMF report into the Colab Files panel so the exact path is */content/MOLDOVA.pdf*.
3. In Colab, open *Secrets* (key icon), create a secret named *GeminiAPI*, enter your Gemini API key, and enable notebook access to the secret.
4. Connect to a Colab runtime with internet access. Run the *14 code cells in order*, starting at Cell 1. The notebook installs its additional Python packages where required.
5. Review Cell 14 for the output-file checklist and validation results. Inspect the economic indicators and cited source pages manually before using the findings in the report.

Do *not* paste the API key into the notebook or upload it with the submission. The notebook reads it securely using google.colab.userdata.get("GeminiAPI").

> *Model note:* The configured model ID is gemini-3.5-flash-lite. Running the notebook requires that this model be available to the supplied Gemini API key. Temporary API errors are retried, and successful responses are cached.

## Notebook structure

| Cell | Purpose |
|---|---|
| 1 | Environment setup and imports |
| 2 | File paths, Gemini API access, response caching and retries |
| 3 | PDF text extraction, cleaning and page tracking |
| 4 | Token-aware chunking (400-token target; 50-token overlap) |
| 5 | Executive summary and major-section summaries |
| 6 | LLM-as-a-Judge evaluation of summaries |
| 7 | Seven-theme financial stability frequency analysis |
| 8 | Six economic strengths and six vulnerabilities |
| 9 | Seven-field economic indicator JSON and source validation |
| 10 | Economic trends, long-format data and Task 2 checks |
| 11 | Local sentence embeddings and FAISS index |
| 12 | Grounded question answering, single-query and multi-query RAG comparison |
| 13 | Four-panel financial dashboard (350 DPI export) |
| 14 | Saved-output audit and assignment validation |

## Saved results

All generated outputs are placed under */content/moldova_outputs/*, including:

- *Task 1:* document_chunks.json, executive_summary.json, section_summaries.json, section_evaluations.json and supporting validation files.
- *Task 2:* thematic_distribution.json, qualitative_risk_insights.json, core_indicators.json, indicator_source_metadata.json, economic_trends.json, economic_trends_long.csv and evaluation files.
- *Task 3:* moldova_faiss.index, rag_index_metadata.json, rag_evaluation_results.json, rag_comparison.json and rag_comparison_summary.json.
- *Task 4:* dashboard_data.csv, plus the dashboard figure in the dashboard/ subfolder as moldova_university_dash…

- The cache/ subfolder stores prior Gemini responses to avoid unnecessary repeated API calls. *Colab runtime storage is temporary:* download the outputs required for submission before disconnecting or resetting the runtime.

## Interpretation and limitations

The notebook generated 226 overlapping chunks from the 100-page report and produced 24 section summaries. It evaluates numerical extraction against IMF evidence and records unavailable indicators as null rather than substituting different financial measures. The Tier 1 capital ratio is not treated as interchangeable with the overall capital adequacy ratio.

The RAG comparison evaluates four questions and reports retrieval and judge-based measures; results should not be generalised to other documents without further testing. Automated scores do not independently prove factual correctness. Financial tables, page citations, report periods and forecast values require manual source verification. In particular, distinguish historical observations from IMF estimates and projections.
## Source and attribution

International Monetary Fund (2026) Republic of Moldova: 2025 Article IV Consultation—Press Release; Staff Report; and Statement by the Alternate Executive Director. IMF Country Report No. 26/59.

Analysis files and charts are produced by the notebook from this report. The accompanying written submission should explain and critically interpret the results in the student's own words and cite the primary IMF source.
