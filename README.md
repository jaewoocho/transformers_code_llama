![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/364cc4ae-723c-49d0-831b-871af67797cc)

# 00. Code Llama: Open Foundation Models for Code - Meta AI 
https://ai.meta.com/research/publications/code-llama-open-foundation-models-for-code/

# 01. Overview
  - The paper, titled "Code Llama: Open Foundation Models for Code," presents Code Llama, a family of large language models specifically designed for code generation and infilling tasks. These models, derived from Llama 2, aim to provide state-of-the-art performance in code-related tasks, including code completion and generation in multiple programming languages, especially Python.

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/b564e8e8-d427-4089-90bb-a2efa6a8378c)


The major topic of the paper is to introduce these three opensource models to be specialized in programming and specific tasks
1. Code Llama
2. Code Llama -Instruct
3. Code Llama -Python
   
## Context and Problem Addressed
  - The motivation behind Code Llama stems from the increasing proficiency of large language models (LLMs) in various applications, particularly those involving a blend of natural and domain-specific language. In the realm of coding, tasks like program synthesis, code completion, debugging, and documentation generation are becoming more prevalent. However, the challenge lies in effectively leveraging LLMs for these tasks, especially given the specialized terminology and syntax in programming.

## Approach
  - The authors approach this problem by building on the Llama 2 model, applying a series of training and fine-tuning steps. This includes code-training from foundation models, introducing an infilling training regime, and fine-tuning for handling long input contexts. Another key aspect is instruction fine-tuning, which improves the model's safety, helpfulness, and ability to follow instructions.

## Solution and Implementation
1. Code-Training: Code Llama is initialized with Llama 2 and then trained on a large dataset predominantly consisting of code. This approach significantly improves the model's proficiency in code generation compared to training from scratch.

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/b901f6b4-a994-4418-a0ec-bc6b5b29c608)

2. Infilling: The models are trained to predict missing parts of a program, beneficial for real-time completion in IDEs or generating in-code documentation.
![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/fea6a9ff-8135-483e-81c5-0d0fbbc124d5)


3. Long Context Fine-Tuning: The models are fine-tuned to handle contexts significantly longer than the standard lengths, allowing for more complex code synthesis and completion tasks.

4. Instruction Fine-Tuning: Models are further fine-tuned with human instruction data, enhancing their ability to follow user instructions accurately and safely.

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/e05b7b80-c0c2-472a-8fda-c95bfd68c4f7)


# 02. Discussion Question for the Class: #1
  - What is the estimated number of parameters in the largest version of the Llama2 language model?
    - A) 7 Billion parameters
    - B) 13 Billion parameters
    - C) 34 Billion parameters
    - D) 70 Billion parameters

  
<details>
    <summary>Answer: </summary>
  
    D) 70 Billion parameters
</details>



## Results 
- Code Llama exhibits state-of-the-art performance on several code benchmarks. Notably, the Python-specialized version outperforms larger models on Python coding benchmarks. The models also demonstrate robustness in handling long sequences and effectively support infilling tasks. The instruction fine-tuning improves safety and helpfulness without significantly compromising code generation capabilities. In summary, Code Llama represents a significant step forward in the application of LLMs for coding tasks, offering improvements in code generation, infilling, and handling of long input contexts, along with enhanced safety and instruction-following capabilities.

- HumanEval: A benchmark comprising Python programming problems to evaluate the effectiveness of code synthesis models in generating function bodies that pass given test cases.
- MBPP (Mostly Basic Python Problems): A dataset of basic Python programming challenges designed to assess a code generation model's ability to solve elementary coding tasks.
- APPS (Algorithms and Programming Problems for Synthesis): A collection of complex programming problems from various computer science disciplines, used to test the advanced problem-solving capabilities of code generation models.

1. Python Code Generation: Code Llama passes scores on the Human Eval, MBPP, APPS

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/c4c5af2e-8793-4b27-8fbe-5be217e96226)
![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/7066f815-2d46-47bf-aef9-c90fc38dc40e)


2. Multilingual evaluation

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/9ce81426-31fd-498c-8990-2a85d3bd3f15)


3. Infilling evaluations

![image](https://github.com/jaewoocho/transformers_code_llama/assets/25238652/c514774e-3e71-4a66-be32-b4cfaf8cb7f5)



# 03. Archiecture Overview
  - Prepare a formal pseudocode description of the proposed model, indicate how it differs from previous models
---
Algorithm: Code Llama Specialization
Input: Pretrained Llama 2 model, Code-heavy dataset, Python-heavy dataset, Instruction data
Output: Specialized Code Llama Models (Code Llama, Code Llama - Python, Code Llama - Instruct)

// Initialize Code Llama with Pretrained Llama 2 Model
function InitializeCodeLlama(pretrainedModel):
    CodeLlama = pretrainedModel
    return CodeLlama

// Specialize for code generation
function SpecializeForCode(CodeLlama, codeDataset):
    for each epoch in trainingEpochs:
        Train CodeLlama on codeDataset with autoregressive objective
    return CodeLlama

// Introduce Infilling Capability
function IntroduceInfilling(CodeLlama, infillingDataset):
    Train CodeLlama on infillingDataset with both autoregressive and infilling objective
    return CodeLlama

// Extend for Long Context Handling
function LongContextFineTuning(CodeLlama, longContextDataset):
    Modify CodeLlama to handle larger input sequences
    Train on longContextDataset
    return CodeLlama

// Fine-Tune with Instruction Data
function InstructionFineTuning(CodeLlama, instructionDataset):
    Train CodeLlama on instructionDataset for enhanced instruction-following
    return CodeLlama

// Main Execution
Llama2 = LoadPretrainedModel()
CodeLlama = InitializeCodeLlama(Llama2)

// Code Training
CodeLlama = SpecializeForCode(CodeLlama, codeDataset)

// Python Specialization
CodeLlama_Python = SpecializeForCode(CodeLlama, PythonDataset)

// Infilling and Long Context
CodeLlama = IntroduceInfilling(CodeLlama, infillingDataset)
CodeLlama = LongContextFineTuning(CodeLlama, longContextDataset)
CodeLlama_Python = LongContextFineTuning(CodeLlama_Python, longContextDataset)

// Instruction Fine-Tuning
CodeLlama_Instruct = InstructionFineTuning(CodeLlama, instructionDataset)

return CodeLlama, CodeLlama_Python, CodeLlama_Instruct

---
Key Differences from Previous Models:
- Foundation Model Utilization: Unlike models trained from scratch on code, Code Llama starts with a pre-trained Llama 2 model, leveraging its existing natural language understanding and knowledge.
- Infilling Training: Code Llama introduces infilling training, allowing it to predict missing parts of code, which is not a standard feature in most traditional LLMs.
- Long Context Fine-Tuning: This step significantly extends the model's ability to process much longer sequences than the standard lengths used in Llama 2, enhancing its applicability to complex code synthesis tasks.
- Instruction Fine-Tuning: This step is specifically focused on improving the model's capability to follow human instructions accurately and safely, which is a specialized enhancement compared to general-purpose LLMs.

# 04. Question #2
  - How will infilling capability in models like Code Llama impact novice programmers' experience?
  - A) Greatly reduce learning curve
  - B) No significant impact
  - C) Increase reliance on AI
  - D) Potentially hinder learning
<details>
    <summary>Answer: </summary>
    
    A) Greatly reduce learning curve
    
    Infilling in models like Code Llama can provide real-time code suggestions and documentation assistance, making coding more accessible and understandable for novice programmers, thereby potentially reducing the learning curve.

  </details>

# 05. Critical Analysis
  - Answer one or more of the following questions: What was overlooked by the authors? What could have been developed further? Were there any errors? Have others disputed the findings?
  - In a critical analysis of the "Code Llama" paper, the most significant area that appears to have been overlooked or warrants further development is the Depth of Responsible AI and Safety Considerations:
  - Potential Oversight: While the paper briefly touches upon responsible AI and safety measures, it doesn't delve deeply into the complex ethical implications and potential risks associated with advanced code-generating models. Given the capability of Code Llama to produce complex code, the nuances of how this might be exploited for unethical purposes (like creating malware) or lead to unintentional biases in code generation are not exhaustively explored.
  - Further Development Needed: The paper could benefit from a more detailed exploration of the mechanisms and strategies implemented to prevent the generation of harmful or unethical code. This includes discussing how the model detects and handles requests for malicious code, how it's trained to avoid introducing security vulnerabilities, and what measures are in place to ensure the fairness and unbiased nature of its code outputs.
  - Lack of Empirical Evidence: There seems to be a lack of extensive empirical evidence demonstrating the model's response in ethically ambiguous or high-risk scenarios. Including detailed case studies or testing the model against a set of ethically challenging prompts could provide greater insight into its safety features.
  - Community Response: As of my last update, there haven't been widely acknowledged errors or disputes about the findings in the AI community. However, the AI ethics community often raises concerns about the potential misuse of such technologies, and these viewpoints might provide valuable feedback for refining the model's safety protocols.
  - In summary, while "Code Llama" marks a significant step forward in LLMs for coding, it could be improved with a more in-depth and nuanced discussion on ethical and safety aspects, considering the potential risks and societal impact of such advanced code-generating AI systems.

# 06. Code Demonstration
  - Google Colab: https://colab.research.google.com/drive/1xeWWt2jV1yqkxPMTO1U98wX5LQl9d9Pr?usp=sharing 
    
# 07. Paper Citation
  - Paper Title: Code Llama: Open Foundation Models for Code
  - Authors: Baptiste Rozière† , Jonas Gehring† , Fabian Gloeckle†,∗ , Sten Sootla† , Itai Gat, Xiaoqing Ellen Tan, Yossi Adi, Jingyu Liu, Tal Remez, Jérémy Rapin, Artyom Kozhevnikov, Ivan Evtimov, Joanna Bitton, Manish Bhatt, Cristian Canton Ferrer, Aaron Grattafiori, Wenhan Xiong, Alexandre Défossez, Jade Copet, Faisal Azhar, Hugo Touvron, Louis Martin, Nicolas Usunier, Thomas Scialom, Gabriel Synnaeve†
  - Link: https://ai.meta.com/research/publications/code-llama-open-foundation-models-for-code/
  - APA style Citation: Rozière, B., Gehring, J., Gloeckle, F., Sootla, S., Gat, I., Tan, X. E., Adi, Y., Liu, J., Remez, T., Rapin, J., ... & Synnaeve, G. (2023). Code Llama: Open Foundation Models for Code. Meta AI. Retrieved from [https://github.com/facebookresearch/codellama](https://ai.meta.com/research/publications/code-llama-open-foundation-models-for-code/)

# 08. Resource links
  - Repository Citation: The accompanying repository for the Code Llama models and additional resources can be found at: GitHub - [facebookresearch/codellama](https://github.com/meta-llama/codellama)https://github.com/meta-llama/codellama
  - Introducing Code Llama, a state-of-the-art large language model for coding: https://ai.meta.com/blog/code-llama-large-language-model-coding/
  - About Code Llama: https://codellama.dev/about
  - Code Llama on Huggingface: https://huggingface.co/codellama
  - Code Llama access: https://huggingface.co/codellama/CodeLlama-7b-hf
  - How To Use Code Llama: https://www.codecademy.com/article/how-to-use-code-llama
  - Papers Explained 62: Code Llama: https://medium.com/dair-ai/papers-explained-62-code-llama-ee266bfa495f

# 09. Video Recording
