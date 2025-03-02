# Local AI Assistant Setup on Unraid

This guide helps you set up a local AI assistant using two containers: **ollama** and **Grist**.

---

## 1. ollama Container

- **Install:**  
  - Get ollama from the Community Apps store in Unraid (use joly0's Repository).

- **Configure for Nvidia GPU:**  
  - In the container's Advanced View, add:
    - **Extra Parameters:**  
      ```
      --runtime=nvidia
      ```
    - **Variables:**  
      - `NVIDIA_VISIBLE_DEVICES`: `all`  
      - `NVIDIA_DRIVER_CAPABILITIES`: `all`

- **Install a Model:**  
  - Open the ollama container console.
  - Install a qwen2.5-coder model that fits your hardware. For example, the [7b model](https://ollama.com/library/qwen2.5-coder:7b) works well.

- **Note the Connection:**  
  - Remember the container’s IP address and port (e.g., `10.10.10.100:11434`).

---

## 2. Grist Container

- **Set Up Variables:**

  - **Model Variable:**  
    - `ASSISTANT_MODEL`:  
      ```
      qwen2.5-coder:7b-instruct-q8_0
      ```
    - *Tip:* If you're not sure which model to use, open the ollama console, type `ollama list`, and copy the model name you want.

  - **Endpoint Variable:**  
    - `ASSISTANT_CHAT_COMPLETION_ENDPOINT`:  
      ```
      http://YOUR-UNRAID-IP-ADDRESS:11434/v1/chat/completions
      ```

Now you’re all set to use your local AI assistant on Unraid!
