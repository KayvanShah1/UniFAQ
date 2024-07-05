# UniFAQ: Fine-Tuned LLM based FAQ Generation for University Admissions

![Banner](/assets/img/FAQ_banner.png)

## Overview

In today's digital landscape, Large Language Models (LLMs) have revolutionized the way we process and generate text. From chatbots to content creation, their applications are vast and ever-growing. This project dives into one such compelling application: using LLMs to generate Frequently Asked Questions (FAQs) from graduate school admission requirements for Master of Science in Computer Science (MSCS) programs.

## Background

Imagine being a prospective student navigating through countless university websites, each with its own set of admission criteria. The process is overwhelming and time-consuming. Here’s where our project steps in. By leveraging the power of LLMs, we aim to simplify this journey. We investigated the performance of several top-tier language models — `T5-large`, `BART-large`, `Mistral 7b`, `LLaMA-2`, and `LLaMA-3` in generating FAQs that mirror real-world admission inquiries.

## Objective

<!-- Our goal is ambitious yet clear: develop an advanced natural language processing system capable of autonomously generating high-quality FAQs for university websites. By aiming for a 10% increase in FAQ accuracy and relevance compared to a baseline T5 transformer model, we strive to make a significant impact on how prospective students access and understand admission information. -->

Our goal is to develop an advanced natural language processing system that can autonomously generate high-quality FAQs for university websites. By leveraging the power of large language models (LLMs) such as T5-large, BART-large, LLaMA-2, and LLaMA-3, we aim to transform complex admission texts into structured, easily accessible FAQs. This project seeks to identify the most effective models for this task and explores innovative fine-tuning methods, including `Quantized Low-Rank Adaptation` (Q-LoRA) and `Parameter-Efficient Fine-Tuning` (PEFT), to optimize performance on limited hardware resources. Ultimately, we aim to significantly enhance the way prospective students access and understand admission information.

## Implementation
1. **Data Collection**:
   - We compiled a list of the top 150 US universities for computer science, based on USNews rankings.
   - Using the BeautifulSoup library, we scraped each university's website for admission requirements and existing FAQs.
   - This data was then structured into a JSON file, ready for training our models.

   ![JSON DATA SAMPLE](/assets/img/json_sample.png)

2. **Text Summarization & Prompt Engineering**:
    - Utilized `GPT-3.5` for summarizing content, ensuring it was concise and primed for effective FAQ generation.
    - Context Optimization: Summarized the context based on ground truth, removing redundant text to streamline information.
    - Instructional Fine-Tuning: Developed and coded instruction prompts to fine-tune LLMs, significantly improving the relevance and quality of the generated FAQs.
    
    <br>

    ![Flowchart](/assets/img/text_summary_gpt.drawio.png)

    <br>

    ![Summary Sample](/assets/img/summarization_sample.png)

2. **Dataset Preparation**:
   - Our dataset was split into training, validation, and testing sets in the ratio of 80%:10%:10%, ensuring a robust evaluation process.

3. **Model Selection and Fine-Tuning**:
   - We started by choosing some of the most advanced language models available: `T5-large`, `Mistral 7b`, `BART-large`, `LLaMA-2`, and `LLaMA-3`.
   - Each model was meticulously fine-tuned using data specifically tailored to admission-related questions, ensuring the generated FAQs are both relevant and accurate.
   - **Integrating QLoRA & PEFT**: To enhance the quality of our FAQs, we integrated `Quantized Low-Rank Adaptation` (QLoRA) `Parameter-Efficient Fine-Tuning` (PEFT). This technique allowed us to fine-tune the models more efficiently, resulting in higher quality outputs.

   ![Summary Sample](/assets/img/fine-tuning.drawio.png)

   - Fine-tuned LLAMA2 & LLAMA3 USC CARC high performance computing machines using GPU allocated for a short duration of time.

## Key Findings and Conclusions
- **Performance Comparison**:
    - **BART** consistently outperformed **T5** in generating FAQs, with higher precision, recall, and F1 scores.
    - **T5** struggled to generate FAQs for all universities and had a lower performance across all metrics.
    - Despite some hallucination issues, BART’s generated content was significantly better than T5’s.

    ![BART Model Results](/assets/img/bart_op.png)
    *Figure 1: BART model Generations.*

    ![T5 Model Results](/assets/img/t5.png)
    *Figure 2: T5 model Generations.*

- **LLaMA Models' Superiority**:
    - **LLaMA-2** and **LLaMA-3** models performed the best, producing accurate and relevant FAQs without hallucinations.
    - Both models showed comparable performance, excelling in ROUGE metrics.
    - The BERT F1 scores for LLaMA-2 and LLaMA-3, including zero-shot prompting, were around 0.8, indicating high-quality FAQ generation.

    ![LLAMA Model Results](/assets/img/llama2_3_op.png)
    *Figure 3: LLAMA2 & LLAMA3 model Generations.*

- **Architectural Insights**:
    - **BART** performed better due to its denoising auto-encoder architecture, which is explicitly trained to handle noisy input and read the input bidirectionally.
    - **T5**, with its encoder-decoder architecture, is more suited for generic text-to-text generation but struggled with the specific task of FAQ generation on a small dataset.

- **Dataset and Model Size Considerations**:
    - The smaller dataset favored **BART** over **T5** because of BART's ability to generate from limited data.
    - BART's smaller model size was advantageous for working with the constrained dataset used in this project.

- **Implications of Zero-Shot Prompting**:
    - Experiments indicated that extensive fine-tuning might not be necessary with powerful models like **LLaMA-2** and **LLaMA-3**.
    - This insight suggests potential for significant reductions in computational costs and time in future applications, leveraging zero-shot prompting capabilities.

    ![Zero shot prompting Model Results](/assets/img/0_shot_prompting_op.png)
    *Figure 4: Zero shot prompting model Generations.*

### Performance Metrics Summary

<!-- | Model          | Precision | Recall | F1 Score | ROUGE-1 | ROUGE-2 | ROUGE-L |
|----------------|-----------|--------|----------|---------|---------|---------|
| **BART**       | 0.2820    | 0.1740 | 0.2260   | 0.2943  | 0.1927  | 0.2401  |
| **T5**         | -0.0560   | -0.1160| -0.0860  | 0.1032  | 0.0094  | 0.0898  |
| **LLaMA-2**    | -         | -      | -        | 0.2286  | 0.0772  | 0.1683  |
| **LLaMA-3**    | -         | -      | -        | 0.2418  | 0.0760  | 0.2187  | -->

| Model          | ROUGE-1 | ROUGE-2 | ROUGE-L |
|----------------|---------|---------|---------|
| **BART**       | 0.2943  | 0.1927  | 0.2401  |
| **T5**         | 0.1032  | 0.0094  | 0.0898  |
| **LLaMA-2**    | 0.2286  | 0.0772  | 0.1683  |
| **LLaMA-3**    | 0.2418  | 0.0760  | 0.2187  |

These findings highlight the strengths of different models and their suitability for specific tasks in FAQ generation, providing valuable insights for future developments and applications.

### Outcome

Through this project, we envision a future where navigating university admissions becomes a seamless experience. Prospective students will have quick access to accurate and relevant FAQs tailored to their specific needs, all thanks to the power of LLMs. This innovation promises to simplify the admissions process, making it more accessible and user-friendly.

Join us on this exciting journey as we harness cutting-edge technology to transform the educational landscape, one FAQ at a time.

### Closing Thoughts

The implications of our study extend beyond simplifying university admissions. Similar techniques could be applied to customer service, legal advice, or any field where complex information needs to be distilled into easy-to-understand FAQs. Furthermore, as LLMs continue to advance, their potential to democratize information and make various processes more efficient is enormous.

This project not only advanced our understanding of LLM capabilities but also highlighted the collaborative potential of AI in addressing real-world problems. We encourage the academic community to build on our findings, explore new applications, and continue pushing the boundaries of what these remarkable models can achieve.

## Authors
1. [Kayvan Shah](https://github.com/KayvanShah1) | `MS in Applied Data Science` | `USC`
2. [Sudarshana Rao](https://github.com/SudarshanaSRao) | `MS in Electrical Engineering (Machine Learning & Data Science)` | `USC`

#### LICENSE
This repository is licensed under the `MIT` License. See the [LICENSE](LICENSE) file for details.

#### Disclaimer

<sub>
The content and code provided in this repository are for educational and demonstrative purposes only. The project may contain experimental features, and the code might not be optimized for production environments. The authors and contributors are not liable for any misuse, damages, or risks associated with the direct or indirect use of this code. Users are strictly advised to review, test, and completely modify the code to suit their specific use cases and requirements. By using any part of this project, you agree to these terms.
</sub>