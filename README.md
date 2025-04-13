import openai

openai.api_key = "YOUR_API_KEY"

def chat_with_ai(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']

# مثال
user_input = input("اكتب سؤالك: ")
print(chat_with_ai(user_input))
npm install firebase
// auth.js
import { initializeApp } from "firebase/app";
import { getAuth, createUserWithEmailAndPassword } from "firebase/auth";

const firebaseConfig = {
  apiKey: "API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  // ...
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);

// تسجيل مستخدم جديد
function signUp(email, password) {
  createUserWithEmailAndPassword(auth, email, password)
    .then(userCredential => console.log("تم التسجيل:", userCredential.user))
    .catch(error => console.error("خطأ:", error.message));
<!-- Tailwind Dark Mode Toggle -->
<button onclick="document.documentElement.classList.toggle('dark')">
  تبديل الوضع
</button>

