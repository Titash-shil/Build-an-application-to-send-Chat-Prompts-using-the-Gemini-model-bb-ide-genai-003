
# Build an application to send Chat Prompts using the Gemini model [bb-ide-genai-003](https://www.cloudskillsboost.google/course_templates/1076/labs/488227)

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

Copy & Run the commands in Cloud Shell :

```
export REGION=
```

```



ID="$(gcloud projects list --format='value(PROJECT_ID)')"


cat > SendChatwithoutStream.py <<EOF
import vertexai
from vertexai.generative_models import GenerativeModel, ChatSession

project_id = "$ID"
location = "$REGION"

vertexai.init(project=project_id, location=location)
model = GenerativeModel("gemini-1.0-pro")
chat = model.start_chat()

def get_chat_response(chat: ChatSession, prompt: str) -> str:
    response = chat.send_message(prompt)
    return response.text

prompt = "Hello."
print(get_chat_response(chat, prompt))

prompt = "What are all the colors in a rainbow?"
print(get_chat_response(chat, prompt))

prompt = "Why does it appear when it rains?"
print(get_chat_response(chat, prompt))
EOF

/usr/bin/python3 /home/student/SendChatwithoutStream.py

cat > SendChatwithStream.py <<EOF
import vertexai
from vertexai.generative_models import GenerativeModel, ChatSession

project_id = "$ID"
location = "$REGION"

vertexai.init(project=project_id, location=location)
model = GenerativeModel("gemini-1.0-pro")
chat = model.start_chat()

def get_chat_response(chat: ChatSession, prompt: str) -> str:
    text_response = []
    responses = chat.send_message(prompt, stream=True)
    for chunk in responses:
        text_response.append(chunk.text)
    return "".join(text_response)

prompt = "Hello."
print(get_chat_response(chat, prompt))

prompt = "What are all the colors in a rainbow?"
print(get_chat_response(chat, prompt))

prompt = "Why does it appear when it rains?"
print(get_chat_response(chat, prompt))
EOF


/usr/bin/python3 /home/student/SendChatwithStream.py
```


# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
