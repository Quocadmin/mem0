<p align="center">
  <a href="https://github.com/mem0ai/mem0">
    <img src="docs/images/banner-sm.png" width="800px" alt="Mem0 - The Memory Layer for Personalized AI">
  </a>
</p>
<p align="center" style="display: flex; justify-content: center; gap: 20px; align-items: center;">
  <a href="https://trendshift.io/repositories/11194" target="blank">
    <img src="https://trendshift.io/api/badge/repositories/11194" alt="mem0ai%2Fmem0 | Trendshift" width="250" height="55"/>
  </a>
</p>

<p align="center">
  <a href="https://mem0.ai">Learn more</a>
  ·
  <a href="https://mem0.dev/DiG">Join Discord</a>
  ·
  <a href="https://mem0.dev/demo">Demo</a>
  ·
  <a href="https://mem0.dev/openmemory">OpenMemory</a>
</p>

<p align="center">
  <a href="https://mem0.dev/DiG">
    <img src="https://dcbadge.vercel.app/api/server/6PzXDgEjG5?style=flat" alt="Mem0 Discord">
  </a>
  <a href="https://pepy.tech/project/mem0ai">
    <img src="https://img.shields.io/pypi/dm/mem0ai" alt="Mem0 PyPI - Downloads">
  </a>
  <a href="https://github.com/mem0ai/mem0">
    <img src="https://img.shields.io/github/commit-activity/m/mem0ai/mem0?style=flat-square" alt="GitHub commit activity">
  </a>
  <a href="https://pypi.org/project/mem0ai" target="blank">
    <img src="https://img.shields.io/pypi/v/mem0ai?color=%2334D058&label=pypi%20package" alt="Package version">
  </a>
  <a href="https://www.npmjs.com/package/mem0ai" target="blank">
    <img src="https://img.shields.io/npm/v/mem0ai" alt="Npm package">
  </a>
  <a href="https://www.ycombinator.com/companies/mem0">
    <img src="https://img.shields.io/badge/Y%20Combinator-S24-orange?style=flat-square" alt="Y Combinator S24">
  </a>
</p>

<p align="center">
  <a href="https://mem0.ai/research"><strong>📄 Building Production-Ready AI Agents with Scalable Long-Term Memory →</strong></a>
</p>
<p align="center">
  <strong>⚡ +26% Accuracy vs. OpenAI Memory • 🚀 91% Faster • 💰 90% Fewer Tokens</strong>
</p>

##  🔥 Research Highlights
- **+26% Accuracy** over OpenAI Memory on the LOCOMO benchmark
- **91% Faster Responses** than full-context, ensuring low-latency at scale
- **90% Lower Token Usage** than full-context, cutting costs without compromise
- [Read the full paper](https://mem0.ai/research)

# Introduction

[Mem0](https://mem0.ai) ("mem-zero") enhances AI assistants and agents with an intelligent memory layer, enabling personalized AI interactions. It remembers user preferences, adapts to individual needs, and continuously learns over time—ideal for customer support chatbots, AI assistants, and autonomous systems.

### Key Features & Use Cases

**Core Capabilities:**
- **Multi-Level Memory**: Seamlessly retains User, Session, and Agent state with adaptive personalization
- **Developer-Friendly**: Intuitive API, cross-platform SDKs, and a fully managed service option

**Applications:**
- **AI Assistants**: Consistent, context-rich conversations
- **Customer Support**: Recall past tickets and user history for tailored help
- **Healthcare**: Track patient preferences and history for personalized care
- **Productivity & Gaming**: Adaptive workflows and environments based on user behavior

## 🚀 Quickstart Guide <a name="quickstart"></a>

Choose between our hosted platform or self-hosted package:

### Hosted Platform

Get up and running in minutes with automatic updates, analytics, and enterprise security.

1. Sign up on [Mem0 Platform](https://app.mem0.ai)
2. Embed the memory layer via SDK or API keys

### Self-Hosted (Open Source)

Install the sdk via pip:

```bash
pip install mem0ai
```

Install sdk via npm:
```bash
npm install mem0ai
```

### Basic Usage

Mem0 requires an LLM to function, with `gpt-4o-mini` from OpenAI as the default. However, it supports a variety of LLMs; for details, refer to our [Supported LLMs documentation](https://docs.mem0.ai/components/llms/overview).

First step is to instantiate the memory:

```python
from openai import OpenAI
from mem0 import Memory

openai_client = OpenAI()
memory = Memory()

def chat_with_memories(message: str, user_id: str = "default_user") -> str:
    # Retrieve relevant memories
    relevant_memories = memory.search(query=message, user_id=user_id, limit=3)
    memories_str = "\n".join(f"- {entry['memory']}" for entry in relevant_memories["results"])

    # Generate Assistant response
    system_prompt = f"You are a helpful AI. Answer the question based on query and memories.\nUser Memories:\n{memories_str}"
    messages = [{"role": "system", "content": system_prompt}, {"role": "user", "content": message}]
    response = openai_client.chat.completions.create(model="gpt-4o-mini", messages=messages)
    assistant_response = response.choices[0].message.content

    # Create new memories from the conversation
    messages.append({"role": "assistant", "content": assistant_response})
    memory.add(messages, user_id=user_id)

    return assistant_response

def main():
    print("Chat with AI (type 'exit' to quit)")
    while True:
        user_input = input("You: ").strip()
        if user_input.lower() == 'exit':
            print("Goodbye!")
            break
        print(f"AI: {chat_with_memories(user_input)}")

if __name__ == "__main__":
    main()
```

For detailed integration steps, see the [Quickstart](https://docs.mem0.ai/quickstart) and [API Reference](https://docs.mem0.ai/api-reference).

## 🔗 Integrations & Demos

- **ChatGPT with Memory**: Personalized chat powered by Mem0 ([Live Demo](https://mem0.dev/demo))
- **Browser Extension**: Store memories across ChatGPT, Perplexity, and Claude ([Chrome Extension](https://chromewebstore.google.com/detail/onihkkbipkfeijkadecaafbgagkhglop?utm_source=item-share-cb))
- **Langgraph Support**: Build a customer bot with Langgraph + Mem0 ([Guide](https://docs.mem0.ai/integrations/langgraph))
- **CrewAI Integration**: Tailor CrewAI outputs with Mem0 ([Example](https://docs.mem0.ai/integrations/crewai))

## 📚 Documentation & Support

- Full docs: https://docs.mem0.ai
- Community: [Discord](https://mem0.dev/DiG) · [Twitter](https://x.com/mem0ai)
- Contact: founders@mem0.ai

## Citation

We now have a paper you can cite:

```bibtex
@article{mem0,
  title={Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory},
  author={Chhikara, Prateek and Khant, Dev and Aryan, Saket and Singh, Taranjeet and Yadav, Deshraj},
  journal={arXiv preprint arXiv:2504.19413},
  year={2025}
}
```

## ⚖️ License

Apache 2.0 — see the [LICENSE](LICENSE) file for details.


Mem0 là gì?
Mem0 là một "lớp bộ nhớ" (memory layer) dành cho AI, giúp cho các trợ lý AI và các agent AI trở nên cá nhân hóa hơn. Nghĩa là, AI có thể ghi nhớ sở thích, lịch sử tương tác và thói quen của người dùng, nhờ vậy phản hồi trở nên tự nhiên, thông minh và sát với nhu cầu thực tế hơn.

Ví dụ: Chatbot có thể nhớ bạn đã hỏi gì trước đó, hay bạn thích phong cách trả lời như thế nào; AI quản lý lịch sử chăm sóc khách hàng, game hoặc công cụ làm việc nhớ được những lần sử dụng trước của bạn để đưa ra trải nghiệm phù hợp.

Dự án này giải quyết vấn đề gì?
Thông thường, AI không nhớ lâu về các tương tác trước đó (vì giới hạn ngữ cảnh hoặc chi phí lưu trữ dữ liệu). Mem0 tạo ra một lớp ghi nhớ hiệu quả, nhanh hơn, tiết kiệm chi phí hơn, và chính xác hơn so với các giải pháp bộ nhớ truyền thống của AI như OpenAI Memory.

Một số điểm mạnh nổi bật:

Tăng 26% độ chính xác khi ghi nhớ so với OpenAI Memory trên benchmark LOCOMO

Phản hồi nhanh hơn 91%

Giảm 90% chi phí token (bộ nhớ ngữ cảnh) so với giải pháp lưu trữ toàn bộ ngữ cảnh

Tính năng chính
Ghi nhớ đa cấp độ: Lưu trữ trạng thái người dùng, phiên làm việc, và agent riêng biệt

Dễ tích hợp: Có API rõ ràng, hỗ trợ nhiều nền tảng, và cả dịch vụ quản lý sẵn sàng sử dụng (hosted)

Tương thích nhiều LLM: Hoạt động tốt với nhiều mô hình ngôn ngữ lớn (LLM) như GPT-4, Claude, v.v.

Ứng dụng thực tế
Trợ lý AI (AI Assistant): Nhớ nội dung các cuộc trò chuyện cũ để trả lời liền mạch hơn

Chăm sóc khách hàng: Ghi nhớ các ticket cũ và lịch sử khách hàng

Y tế: Theo dõi thông tin bệnh nhân, sở thích điều trị

Năng suất & Game: Ghi nhớ hành vi người dùng, cá nhân hóa trải nghiệm làm việc hoặc chơi game

Cách sử dụng nhanh (Quickstart)
Bạn có thể chọn:

Dùng nền tảng quản lý sẵn (Hosted Platform): Đăng ký tài khoản tại mem0.ai, lấy API key và tích hợp vào app của bạn

Tự host mã nguồn (Self-hosted):

Python: pip install mem0ai

NodeJS: npm install mem0ai

Ví dụ sử dụng cơ bản bằng Python
python
Sao chép
Chỉnh sửa
from openai import OpenAI
from mem0 import Memory

openai_client = OpenAI()
memory = Memory()

def chat_with_memories(message: str, user_id: str = "default_user") -> str:
    # Lấy ra những "ký ức" liên quan từ bộ nhớ
    relevant_memories = memory.search(query=message, user_id=user_id, limit=3)
    memories_str = "\n".join(f"- {entry['memory']}" for entry in relevant_memories["results"])

    # Gửi prompt cho AI, đính kèm "ký ức"
    system_prompt = f"Bạn là AI thân thiện. Trả lời dựa trên câu hỏi và ký ức của người dùng:\n{memories_str}"
    messages = [{"role": "system", "content": system_prompt}, {"role": "user", "content": message}]
    response = openai_client.chat.completions.create(model="gpt-4o-mini", messages=messages)
    assistant_response = response.choices[0].message.content

    # Lưu hội thoại mới vào bộ nhớ
    messages.append({"role": "assistant", "content": assistant_response})
    memory.add(messages, user_id=user_id)

    return assistant_response
Xem thêm: Hướng dẫn nhanh và API Reference.

Demo, tài liệu & hỗ trợ
Demo thử: mem0.dev/demo

Tài liệu chi tiết: docs.mem0.ai

Discord cộng đồng: mem0.dev/DiG

Email hỗ trợ: founders@mem0.ai

Kết luận ngắn gọn
Nếu bạn làm việc với AI, chatbot, hoặc muốn app của mình biết nhớ và cá nhân hóa, Mem0 là nền tảng dễ tích hợp và tối ưu chi phí mà bạn nên thử.
Bạn có thể thử nghiệm ngay với bản open source hoặc dùng dịch vụ hosted.
