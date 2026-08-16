# n8n-image-generation-bot
An n8n workflow that automates AI image generation using Hugging Face FLUX.1-schnell and automatically uploads the generated images to Google Drive.



# n8n Image Generation Bot

An AI image-generation automation workflow built with **n8n**, **Hugging Face FLUX.1-schnell**, and **Google Drive**.

The workflow sends a text prompt to an AI image-generation model through an HTTP request, receives the generated image as binary data, and automatically uploads the result to Google Drive.

---

## 🚀 Demo

A recorded demonstration of the workflow is included in this repository.

**[▶ Watch the Demo](./assets/demo.mp4)**

---

## 🧠 How It Works

The workflow consists of three main stages:

```text
Text Prompt
     │
     ▼
┌─────────────────────────┐
│      n8n Trigger        │
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│     HTTP Request        │
│                         │
│ Hugging Face Inference  │
│    FLUX.1-schnell       │
└────────────┬────────────┘
             │
             │ Generated image
             ▼
┌─────────────────────────┐
│      Google Drive       │
│                         │
│   Upload generated      │
│        image            │
└─────────────────────────┘
```

### 1. Workflow Trigger

The workflow starts with an n8n manual trigger, allowing the workflow to be executed during development and testing.

### 2. AI Image Generation

An **HTTP Request** node sends a `POST` request to the Hugging Face inference endpoint for **FLUX.1-schnell**.

The prompt is provided as JSON:

```json
{
  "inputs": "man sailing a ship"
}
```

The model processes the prompt and returns the generated image.

### 3. Image Handling

The generated image is received by n8n as **binary image data**.

The binary output is then passed directly to the Google Drive node.

### 4. Google Drive Upload

The **Google Drive** node automatically uploads the generated image to cloud storage.

The resulting file is stored as a PNG image in Google Drive.

---

## 🛠️ Technologies Used

* **n8n** — Workflow automation and orchestration
* **Hugging Face** — AI inference
* **FLUX.1-schnell** — Text-to-image generation model
* **Google Drive** — Cloud storage
* **HTTP / REST API** — Communication with the image-generation service
* **JSON** — Request data format

---

## 🖼️ Example

The workflow was tested using the prompt:

```text
man sailing a ship
```

The generated image was successfully returned by the inference API and automatically uploaded to Google Drive.

![Generated Image](./assets/generated-image.png)

---

## 📸 Project Screenshots

### Workflow

![n8n Workflow](./assets/workflow.png)

The complete n8n workflow connecting the trigger, image-generation API, and Google Drive.

### HTTP Request

![HTTP Request](./assets/http-request.png)

The HTTP Request node sends the prompt to the Hugging Face FLUX.1-schnell inference endpoint and receives the generated image.

### Google Drive Output

![Google Drive Output](./assets/google-drive-output.png)

The generated image is automatically uploaded to Google Drive after the API request completes successfully.

---

## 🔐 Security

No API keys, access tokens, or private credentials are included in this repository.

Credentials should always be stored securely using n8n's credential-management system or environment variables rather than being hard-coded into workflows or committed to GitHub.

---

## ⚠️ Project Status

The original workflow was developed and tested using a limited hosted n8n trial environment.

The hosted instance is no longer active, so this repository serves as a **project archive and technical demonstration** containing the workflow documentation, screenshots, generated output, and recorded demonstration.

The screenshots and demo document the workflow operating successfully during development.

---

## 🔮 Future Improvements

The workflow could be expanded into a more complete image-generation application by:

* Adding a webhook for dynamic user prompts
* Building a chat-based interface
* Supporting multiple image-generation models
* Allowing users to choose image parameters
* Automatically generating filenames from prompts
* Adding error handling and retry mechanisms
* Returning the generated image directly to the user
* Connecting additional cloud-storage providers
* Adding a frontend interface

---

## 📚 What I Learned

This project provided practical experience with:

* Building workflows with n8n
* Working with REST APIs
* Sending JSON requests
* Integrating AI inference services
* Handling binary data inside automation workflows
* Connecting APIs with cloud-storage services
* Automating multi-step processes
* Managing API credentials securely

---

## 👨‍💻 Project

**Project:** n8n Image Generation Bot
**Purpose:** AI image-generation automation
**Status:** Completed prototype / archived demonstration
