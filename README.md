# NaijaMind

**A fine-tuned language model that understands Nigeria — its languages, its business context, and the way its people actually communicate.**

Generic AI speaks formal English. It doesn't know what "abeg" means, why WhatsApp is a sales channel, or what ₦50k buying power looks like in Lagos. NaijaMind does.

Built by fine-tuning [Qwen 3](https://github.com/QwenLM/Qwen3) on curated Nigerian Pidgin, Nigerian English, and business content. Released under **Apache 2.0** — free for anyone to use, modify, or build on.

---

## Why NaijaMind?

| Generic AI | NaijaMind |
|------------|-----------|
| "Please, could you clarify your request?" | "Abeg, wetin you wan do?" |
| Doesn't understand Pidgin | Native Pidgin English speaker |
| Assumes credit card payments | Knows Paystack, Flutterwave, bank transfer, USSD |
| Generic pricing advice | Knows what ₦500 vs ₦50,000 means in Lagos |
| No local context | Lagos traffic, Abuja rent, PH logistics |

---

## What Makes It Different

- **🗣️ Pidgin English Native** — Understands "sef", "wahala", "no wahala", "abeg", "how far", "wetin dey", "I no sabi", "comot", "dash", and hundreds of local expressions
- **💼 Business Context Aware** — Knows Nigerian payment methods (Paystack, Flutterwave, bank transfer, USSD), WhatsApp-first customer behavior, local pricing psychology, Airtime as currency, "POS" agent network
- **📍 Geographically Grounded** — Lagos traffic patterns, Abuja real estate, Port Harcourt logistics, "Danfo", "Keke NAPEP", "Okada", the difference between "Lagos boy" and "Abuja person"
- **🔓 Open Weights** — Apache 2.0 licensed. Free to use, fine-tune, or build on.

---

## Use Cases

### Customer Support Chatbots
Chatbots that actually sound Nigerian — warm, culturally appropriate, using Pidgin naturally. Handles "Abeg my network don finish, I no fit transfer" or "The POS guy no get change."

### Sales AI
Sales assistants that understand local objections ("Na too much", "I go think about am", "My oga dey come"), pricing expectations, and WhatsApp-based sales funnels.

### Content Generators
Content writers that produce blog posts, social media captions, ad copy in authentic Nigerian English and Pidgin. Understands what Nigerian Twitter finds funny.

### Voice Assistants
Text-to-speech and speech-to-text pipelines tuned for Pidgin and Nigerian-accented English. Foundation for voice agents that interact in local languages.

---

## Model Selection

After thorough research, **Qwen 3** was chosen as the base model. Here's why:

| Criteria | Qwen 3 | DeepSeek | Llama 3 |
|----------|--------|----------|---------|
| **License** | ✅ Apache 2.0 | ⚠️ MIT (V3.2) / Custom (R1) | ⚠️ Llama (restrictions) |
| **Fine-tune Feasibility** | ✅ Dense models 0.6B-32B — easy LoRA/QLoRA | ❌ MoE 671B — impractical to FT | ✅ Dense models — good FT support |
| **Small Model Performance** | ✅ 4B matches 72B on benchmarks | ⚠️ Distilled variants inherit base license | ⚠️ 8B is capable but weaker |
| **Ecosystem** | ✅ Unsloth, Ollama, vLLM, llama.cpp | ⚠️ Good inference, FT docs limited | ✅ Best FT ecosystem |

**Qwen 3 wins on:** Apache 2.0 license, practical fine-tuning on small dense models, and a permissive license that ensures NaijaMind stays open.

---

## Training Approach

### Phase 1: Continued Pre-Training
Adapt Qwen 3's tokenizer and weights to Nigerian Pidgin distribution using causal LM on ~200K Pidgin text segments.

### Phase 2: Instruction Fine-Tuning
Fine-tune with LoRA on ~30K instruction examples — 50% English, 30% Pidgin, 20% code-switched.

### Phase 3: Business Alignment
Specialize on ~50K business-specific dialogues — customer support, sales conversations, content briefs.

**Hardware:** QLoRA on Qwen 3-4B fits on a single RTX 4090 (24GB). Inference runs on any modern laptop via GGUF quantization.

---

## Dataset Sources

| Source | Type | Size |
|--------|------|------|
| BBC News Pidgin | News articles in Pidgin | Large corpus |
| Nairaland | Nigerian forum posts | Millions of posts |
| Nigerian business blogs | Paystack, Flutterwave, Techpoint | 1000s of articles |
| Synthetic dialogues | GPT-4/Claude generated + human reviewed | 50K examples |
| Social media | X/Twitter Nigeria, Reddit r/Nigeria | Large corpus (filtered) |

---

## Quickstart

```bash
# Coming soon — model weights will be available on Hugging Face

# Download a GGUF quantized version
# Run with Ollama
ollama run naijamind
```

### Python

```python
# Coming soon
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained("forge-growth/NaijaMind-4B")
tokenizer = AutoTokenizer.from_pretrained("forge-growth/NaijaMind-4B")

prompt = "Abeg, wetin be the best way to ask customer for feedback for Nigeria?"
inputs = tokenizer(prompt, return_tensors="pt")
outputs = model.generate(**inputs, max_new_tokens=256)
print(tokenizer.decode(outputs[0]))
```

---

## Tech Stack

- **Base Model:** Qwen 3-4B (Apache 2.0)
- **Training:** Unsloth / Hugging Face TRL + PEFT (LoRA/QLoRA)
- **Inference:** Ollama, llama.cpp, vLLM, SGLang
- **Quantization:** GGUF (Q4_K_M, Q5_K_M, Q8_0)
- **Data Processing:** Python, Hugging Face Datasets

---

## Roadmap

- [ ] **Q1 2026:** Dataset collection, cleaning, and annotation
- [ ] **Q2 2026:** Continued pre-training + instruction fine-tuning
- [ ] **Q3 2026:** NaijaMind v1 release on Hugging Face
- [ ] **Q4 2026:** Community feedback, v1.1 improvements, voice integration

---

## License

**Apache 2.0.** Free for any use — personal, research, commercial, or government.

Model weights, training code, and dataset preparation scripts will be published under Apache 2.0.

---

## Built By

**ForgeGrowth** — Building AI that speaks Nigerian.

- Website: [forgegrowth.io](https://forgegrowth.io)
- GitHub: [Forge-Growth](https://github.com/Forge-Growth)
- Email: `naijamind@forgegrowth.io`

---

## Citation

```bibtex
@misc{naijamind2026,
  title = {NaijaMind: A Fine-Tuned Language Model for Nigerian Languages, Pidgin \& Business Context},
  author = {ForgeGrowth},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/Forge-Growth/naijamind}
}
```
