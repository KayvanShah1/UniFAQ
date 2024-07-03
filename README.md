# UniFAQ: Fine-Tuned LLM based FAQ Generation for University Admissions

## Overview

In today's digital landscape, Large Language Models (LLMs) have revolutionized the way we process and generate text. From chatbots to content creation, their applications are vast and ever-growing. This project dives into one such compelling application: using LLMs to generate Frequently Asked Questions (FAQs) from graduate school admission requirements for Master of Science in Computer Science (MSCS) programs.

## Background

Imagine being a prospective student navigating through countless university websites, each with its own set of admission criteria. The process is overwhelming and time-consuming. Here’s where our project steps in. By leveraging the power of LLMs, we aim to simplify this journey. We investigated the performance of several top-tier language models — `T5-large`, `BART-large`, `LLaMA-2`, and `LLaMA-3` in generating FAQs that mirror real-world admission inquiries.

## The Journey
1. **Data Collection**:
   - We compiled a list of the top 150 US universities for computer science, based on USNews rankings.
   - Using the BeautifulSoup library, we scraped each university's website for admission requirements and existing FAQs.
   - This data was then structured into a JSON file, ready for training our models.

   ![JSON DATA SAMPLE](/assets/img/json_sample.png)

2. **Text Summarization & Prompt Engineering**:
    - Utilized `GPT-3.5` for summarizing content, ensuring it was concise and primed for effective FAQ generation.
    - Context Optimization: Summarized the context based on ground truth, removing redundant text to streamline information.
    - Instructional Fine-Tuning: Developed and coded instruction prompts to fine-tune LLMs, significantly improving the relevance and quality of the generated FAQs.
    
    ![Flowchart](/assets/img/txt_summarization.png)
    ![Summary Sample](/assets/img/summarization_sample.png)

2. **Dataset Preparation**:
   - Our dataset was split into training, validation, and testing sets in the ratio of 80%:10%:10%, ensuring a robust evaluation process.

3. **Model Selection and Fine-Tuning**:
   - We started by choosing some of the most advanced language models available: `T5-large`, `BART-large`, `LLaMA-2`, and `LLaMA-3`.
   - Each model was meticulously fine-tuned using data specifically tailored to admission-related questions, ensuring the generated FAQs are both relevant and accurate.

4. **Integrating QLoRA PEFT**:
   - To enhance the quality of our FAQs, we integrated `Quantized Low-Rank Adaptation` (QLoRA) `Parameter-Efficient Fine-Tuning` (PEFT). This technique allowed us to fine-tune the models more efficiently, resulting in higher quality outputs.



## Objective

Our goal is ambitious yet clear: develop an advanced natural language processing system capable of autonomously generating high-quality FAQs for university websites. By aiming for a 10% increase in FAQ accuracy and relevance compared to a baseline T5 transformer model, we strive to make a significant impact on how prospective students access and understand admission information.

## The Outcome

Through this project, we envision a future where navigating through university admissions becomes a seamless experience. Prospective students will have quick access to accurate and relevant FAQs, tailored to their specific needs, all thanks to the power of LLMs.

Join us on this exciting journey as we harness cutting-edge technology to transform the educational landscape, one FAQ at a time.

## Authors
1. [Kayvan Shah](https://github.com/KayvanShah1) | `MS in Applied Data Science` | `USC`

#### LICENSE
This repository is licensed under the `MIT` License. See the [LICENSE](LICENSE) file for details.

#### Disclaimer

<sub>
The content and code provided in this repository are for educational and demonstrative purposes only. The project may contain experimental features, and the code might not be optimized for production environments. The authors and contributors are not liable for any misuse, damages, or risks associated with the direct or indirect use of this code. Users are strictly advised to review, test, and completely modify the code to suit their specific use cases and requirements. By using any part of this project, you agree to these terms.
</sub>