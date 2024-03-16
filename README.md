![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/364cc4ae-723c-49d0-831b-871af67797cc)

# 00. Code Llama: Open Foundation Models for Code - Meta AI

# 01. Overview
  - Five-minute overview providing context, stating the problem the paper is addressing, characterizing the approach, and giving a brief account of how the problem was addressed.
  - The paper, titled "Code Llama: Open Foundation Models for Code," presents Code Llama, a family of large language models specifically designed for code generation and infilling tasks. These models, derived from Llama 2, aim to provide state-of-the-art performance in code-related tasks, including code completion and generation in multiple programming languages, especially Python.
## Context and Problem Addressed
  - The motivation behind Code Llama stems from the increasing proficiency of large language models (LLMs) in various applications, particularly those involving a blend of natural and domain-specific language. In the realm of coding, tasks like program synthesis, code completion, debugging, and documentation generation are becoming more prevalent. However, the challenge lies in effectively leveraging LLMs for these tasks, especially given the specialized terminology and syntax in programming.
## Approach
  - The authors approach this problem by building on the Llama 2 model, applying a series of training and fine-tuning steps. This includes code-training from foundation models, introducing an infilling training regime, and fine-tuning for handling long input contexts. Another key aspect is instruction fine-tuning, which improves the model's safety, helpfulness, and ability to follow instructions.
## Solution and Implementation
### 1. Code-Training: Code Llama is initialized with Llama 2 and then trained on a large dataset predominantly consisting of code. This approach significantly improves the model's proficiency in code generation compared to training from scratch.
### 2. Infilling: The models are trained to predict missing parts of a program, beneficial for real-time completion in IDEs or generating in-code documentation.
### 3. Long Context Fine-Tuning: The models are fine-tuned to handle contexts significantly longer than the standard lengths, allowing for more complex code synthesis and completion tasks.
### 4. Instruction Fine-Tuning: Models are further fine-tuned with human instruction data, enhancing their ability to follow user instructions accurately and safely.
## Results 
- Code Llama exhibits state-of-the-art performance on several code benchmarks. Notably, the Python-specialized version outperforms larger models on Python coding benchmarks. The models also demonstrate robustness in handling long sequences and effectively support infilling tasks. The instruction fine-tuning improves safety and helpfulness without significantly compromising code generation capabilities. In summary, Code Llama represents a significant step forward in the application of LLMs for coding tasks, offering improvements in code generation, infilling, and handling of long input contexts, along with enhanced safety and instruction-following capabilities.


# 02. Question #1
  - Cover first chosen topic, ask a question for the class to discuss
# 03. Archiecture Overview
  - Prepare a formal pseudocode description of the proposed model, indicate how it differs from previous models
# 00. Question #2
  - Cover first chosen topic, ask a question for the class to discuss
# 00. Critical Analysis
  - Answer one or more of the following questions: What was overlooked by the authors? What could have been developed further? Were there any errors? Have others disputed the findings?
# 00. Code Demonstration
  - Make a Jupyter notebook demonstrating using the model/approach
# 00. Citation Paper
  - Cite paper, mention authors, include citation in repo
# 00. Resource links
  - Prepare links of where to go to get more information (other papers, model page, blog posts (e.g. papers with code)), 1 point per link up to 5 points
# 00. Video Recording
