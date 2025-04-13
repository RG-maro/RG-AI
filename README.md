from fastapi import FastAPI, Form
from fastapi.middleware.cors import CORSMiddleware
import openai

openai.api_key = "YOUR_OPENAI_API_KEY"  # استبدله بمفتاحك

app = FastAPI()

# للسماح للواجهة بالتواصل مع الخادم
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # عدلها لاحقاً لأمان أكثر
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

@app.post("/chat/")
async def chat(prompt: str = Form(...)):
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # أو "gpt-4" إن توفر
        messages=[
            {"role": "system", "content": "أنت مساعد ذكي يساعد المستخدمين بالعربية والإنجليزية."},
            {"role": "user", "content": prompt}
        ]
    )
    reply = response['choices'][0]['message']['content']
    return {"response": reply}
uvicorn main:app --reload
curl -X POST -F "prompt=ما هو الذكاء الاصطناعي؟" http://localhost:8000/chat/
