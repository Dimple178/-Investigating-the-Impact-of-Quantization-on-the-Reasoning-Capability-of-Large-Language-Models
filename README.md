# -Investigating-the-Impact-of-Quantization-on-the-Reasoning-Capability-of-Large-Language-Models

## 📌 Executive Summary

This research investigates how quantization affects the reasoning capabilities of Large Language Models (LLMs), aiming to balance computational efficiency and reasoning performance. Quantization—reducing numerical precision (e.g., from float32 to int8)—offers significant savings in memory and power consumption, making LLMs more deployable on resource-limited devices. However, it can degrade performance in tasks requiring high cognitive accuracy.

We evaluated several LLMs across four reasoning-focused datasets:

- **LogiQA**: Logical reasoning  
- **Common Sense QA**: Common-sense reasoning  
- **Social Intelligence QA (SIQA)**: Social and emotional reasoning  
- **AQuA-RAT**: Algebraic reasoning with rationales  

Quantization levels from **2-bit to 32-bit** were tested, and notable accuracy drops were observed at lower bit levels—especially in logic-intensive tasks. Performance generally improved with higher bit precision, plateauing beyond 16 bits. Models like **Mistral 8×7B** and **LLaMA 3 8B** maintained strong reasoning even at reduced precision, showcasing the role of architecture in mitigating quantization loss.

## 🔍 Introduction

Recent advances in NLP have been largely driven by the capabilities of LLMs, which excel at tasks requiring deep reasoning. However, their high computational demands pose a challenge for widespread deployment. **Quantization** has emerged as a practical solution, reducing model size and computational requirements.

While quantization improves efficiency, its impact on reasoning tasks is underexplored. This study evaluates that impact across **four cognitive domains** using specialized datasets and compares two prominent LLM families:

- **MistralAI Models**:
  - `Mistral-7B-Instruct-v0.2`
  - `Mixtral-8x7B-Instruct-v0.1`
  
- **Meta LLaMA Models**:
  - `LLaMA-2-7B-hf`
  - `LLaMA-3-13B-hf`
  - `LLaMA-3-8B`

Each model was quantized to **2, 3, 4, 8, and 16 bits**, and evaluated on:

| Dataset     | Reasoning Type             |
|-------------|-----------------------------|
| LogiQA      | Logical reasoning            |
| CommonSenseQA | Common-sense reasoning     |
| SIQA        | Social and emotional reasoning |
| AQuA-RAT    | Algebra with rationales      |

The results demonstrate that while lower-bit quantization reduces accuracy, especially for logic-heavy tasks, mid-level quantization (e.g., 8 or 16 bits) offers a good trade-off between performance and efficiency.

---

## 🧪 Datasets

| Dataset | Description |
|--------|-------------|
| **LogiQA** | Tests logical consistency through multiple-choice questions. |
| **Common Sense QA** | Assesses common-sense reasoning through general knowledge queries. |
| **SIQA** | Focuses on understanding social interactions and emotional intelligence. |
| **AQuA-RAT** | Requires solving algebra word problems and explaining the reasoning process. |

---

## 🧰 Models Used

- **MistralAI**:
  - `Mistral-7B-Instruct-v0.2`
  - `Mixtral-8x7B-Instruct-v0.1`

- **Meta LLaMA**:
  - `LLaMA-2-7B-hf`
  - `LLaMA-3-13B-hf`
  - `LLaMA-3-8B`

---

## ⚙️ Quantization Levels

Models were quantized at:
- **2-bit**
- **3-bit**
- **4-bit**
- **8-bit**
- **16-bit**
- (Full precision for comparison)

---

## 📊 Key Findings

- Quantization below 4-bit significantly impairs reasoning.
- Logical and mathematical tasks (LogiQA, AQuA) are most sensitive to quantization.
- Models with stronger architectures (e.g., Mixtral, LLaMA 3 8B) retain better performance at low precision.
- Performance stabilizes beyond 16-bit quantization, indicating full precision isn't always necessary.

---

## 💡 Conclusion

This study highlights the delicate balance between efficiency and cognitive strength in LLMs. While quantization is essential for resource-constrained deployment, understanding its limits is key. Mid-range quantization (8–16 bit) offers a sweet spot, and robust model architectures can further minimize losses.

This work serves as a foundation for future research in efficient LLM deployment, especially for applications that demand advanced reasoning under hardware constraints.

---

## 📁 Folder Structure

```bash
.
├── data/                    # Datasets (LogiQA, SIQA, etc.)
├── models/                 # Pretrained + quantized model versions
├── scripts/                # Evaluation, quantization, visualization scripts
├── results/                # Evaluation logs and result summaries
├── README.md               # Project documentation
