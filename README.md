🎓 Workshop: Getting Started with Ollama & Running Llama Models
Presenters:
👨‍💻 Muneer – Your Tech Guide
I'm passionate about AI and open-source tools. I love breaking down complex topics into simple steps and helping others get hands-on with cutting-edge technology like Ollama and Llama models.

👩‍💻 Aishwarya – Making It Clear & Simple
I focus on making technical concepts accessible to everyone. Whether it's explaining how models work or walking through installations, my goal is to make learning AI fun and easy — no jargon, just real results.

Together, we're here to guide you step by step through installing Ollama , running Llama3 , and even setting up integrations — all in a way that’s beginner-friendly and engaging.

🧭 Table of Contents
What is Ollama?
Why Use Ollama?
What You’ll Need Before Starting
How to Install Ollama
Running Llama Models
Customizing Model Behavior
Understanding Responses
Backing Up Outputs to Google Drive
Troubleshooting Common Issues
Want to Help Improve Ollama?
License Info
Get in Touch
Appendix: Ollama Installation Script (for Advanced Users)
1. What is Ollama?
Ollama is an open-source tool that lets you run large language models like Llama , Llama2 , and Llama3 directly on your own computer — no internet required after downloading the model.

It’s fast, private, and perfect for developers, students, and AI enthusiasts who want to experiment with powerful models without relying on APIs or cloud services.

2. Why Use Ollama?
Here’s why Ollama makes life easier:

✅ Runs locally – No internet needed after download
🔐 Private by default – Your data never leaves your device
🚀 Fast and simple – Works great on Mac, Linux, and Windows (via WSL)
🧠 Supports popular models – Like Llama3, one of the smartest open-source models out there
🛠️ Easy to use – Just install and start chatting or coding
🔄 Integrates well – With Python, Google Drive, and more

Whether you want to chat, code, or build apps — Ollama can help.

3. What You’ll Need Before Starting
Before diving in, make sure you have:

💻 Operating System : macOS, Linux, or Windows (use WSL2)
💾 RAM : At least 8GB (16GB+ recommended for smoother experience)
🧰 Basic Terminal Knowledge
🌐 Internet Connection : To download Ollama and models

Once that’s ready, you’re all set!

4. How to Install Ollama
For macOS:
Open Terminal and run:

bash


1
curl -fsSL https://ollama.com/install.sh  | sh
For Linux:
Run these commands:

bash


1
2
sudo apt update
sudo apt install -y ollama
For Windows:
Use Windows Subsystem for Linux (WSL2) and follow the Linux instructions above.

Check if it worked:
bash


1
ollama --version
If you see a version number — you did it! Ollama is now installed.

💡 Note : The full Ollama installation script is included at the end of this document for advanced users or those interested in understanding how the tool is deployed behind the scenes. 

5. Running Llama Models
Let’s try running Llama3 , one of the most advanced open-source models.

Step 1: Download the model
bash


1
ollama pull llama3
Step 2: Start using it
bash


1
ollama run llama3
Now you’re inside a chat interface. Try asking fun questions like:

“Tell me a joke.”
“Explain quantum physics in simple terms.” 

You’ll get real-time responses — powered by AI right on your laptop!

6. Customizing Model Behavior
Want the model to be more creative or stick to facts?

You can adjust settings like:

temperature: Higher = more creative, Lower = more factual
max_tokens: Controls how long the response should be
top_p, frequency_penalty: More advanced controls
Example in Python :

python


1
2
3
4
5
6
7
8
9
import ollama

response = ollama.generate(
    model="llama3",
    prompt="Write a poem about cats.",
    temperature=0.8
)

print(response["response"])
This gives you control over how the model thinks and responds.

7. Understanding Responses
When you ask a question, Ollama generates a response based on what it learned during training.

Examples of things it can do:

📝 Answer questions
💻 Generate code
📚 Summarize text
✍️ Write poems or stories
📊 Explain complex topics

But remember — it’s not always perfect. Sometimes it might guess wrong or even make up answers. Always double-check important info.

8. Backing Up Outputs to Google Drive
Wouldn’t it be nice if every response was saved automatically?

Here’s how to back up your results to Google Drive :

Install rclone – a tool for syncing files to the cloud
Set it up with your Google Drive account
Create a folder to store outputs:
bash


1
mkdir ~/ollama_output
Save a response and sync it:
bash


1
2
ollama generate llama3 "Your question" > ~/ollama_output/response.txt
rclone copy ~/ollama_output remote_drive:/ollama_backup
Now all your AI-generated ideas are safely stored online.

9. Troubleshooting Common Issues
PROBLEM
SOLUTION
Can't download the model
Check your internet connection
Out of memory error
Try smaller models like
llama3:8b
Command not found
Reinstall Ollama or add it to PATH
GPU not working
Make sure CUDA drivers are installed

Still stuck? Ask us during Q&A or check the Ollama GitHub .

10. Want to Help Improve Ollama?
Ollama is open source , so anyone can contribute!

You can:

🔍 Report bugs
💡 Suggest new features
📚 Improve documentation
💻 Submit code changes
Check out their GitHub page and join the community!

11. License Info
Ollama uses the MIT License , which means you can freely use, modify, and share it — even for commercial purposes.

Each model (like Llama3) may have its own license, so always read the fine print before sharing or reusing them.

12. Get in Touch
Have questions or feedback? Feel free to reach out:

📧 Email :

Muneer: muneer@example.com
Aishwarya: aishwarya@example.com
🧑‍💻 LinkedIn : Search for our names
👨‍💻 GitHub : @muneerai / @aishwaryaml

🔗 Ollama Resources :

Website: ollama.com
GitHub: github.com/ollama/ollama
13. Appendix: Ollama Installation Script (Advanced)
Below is the full content of the official Ollama installation script used when you run:

bash


1
curl -fsSL https://ollama.com/install.sh  | sh
This script handles everything from detecting your OS and architecture to installing the correct binaries, setting up systemd services, and configuring GPU support where available.

(Include the raw script content here as a code block or reference.)

🎉 Final Words
We hope this workshop gave you a solid foundation to start exploring Ollama and Llama models .

Remember:

🧠 AI isn’t just for experts
💡 It’s for everyone who wants to learn, create, and innovate

So go ahead — play around with Ollama, ask it anything, and maybe even build something amazing.

Thank you for joining us today — happy experimenting! 🚀
