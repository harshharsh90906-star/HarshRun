# Harsh Run — iPhone IPA banane ka jugaad (bina Mac ke)

Tere paas Mac nahi hai, isliye IPA seedha PC pe nahi ban sakta.
Ye project ek **jugaad** hai jo kaam karta hai:

**Capacitor project (ye folder) → GitHub → Codemagic (free cloud Mac) → unsigned IPA → AltStore (PC) → iPhone**

Paisa: kuch nahi — Codemagic free 500 min/month, AltStore free, Apple ID free.
Ek limit: free Apple ID se install ki hui app **har 7 din me expire** hoti hai.
AltServer PC on rehte hue Wi-Fi pe khud refresh kar deta hai (phone aur PC ek hi Wi-Fi pe hon).

## Step 1 — GitHub pe project dalo (5 min)
1. github.com pe account banao (free).
2. PC pe **GitHub Desktop** install karo (desktop.github.com).
3. GitHub pe naya repo banao — naam: `harsh-run`.
4. GitHub Desktop me repo clone karo, is zip ke saare files us folder me copy karo,
   phir GitHub Desktop me **Commit** → **Publish** dabao.
   (`node_modules` mat dalna — `.gitignore` pehle se hai.)

## Step 2 — Codemagic pe free build (10-15 min)
1. codemagic.io pe **Sign up with GitHub** karo.
2. **Add application** → GitHub → `harsh-run` repo select karo.
3. Workflow select karo: **iOS unsigned IPA** → **Start new build**.
4. Build chalne do. Khatam hote hi **Artifacts** me `HarshRun-unsigned.ipa` milega — download karo.
   (Apple Developer account ya certificate kuch nahi chahiye — build unsigned hota hai.)

## Step 3 — AltStore se iPhone me install karo
1. PC pe altstore.io se **AltStore** install karo.
   Saath me Apple ki site se **iTunes** aur **iCloud** bhi install karo
   (Microsoft Store wale nahi — apple.com/itunes se lo).
2. iPhone me **Developer Mode** on karo:
   Settings → Privacy & Security → Developer Mode → ON → restart.
3. iPhone USB se PC se connect karo. PC pe system tray me **AltServer** → Install AltStore → apna iPhone select karo.
   Apni Apple ID se sign in karo (free ID chalega — password AltServer pe hi rehta hai).
4. iPhone pe **AltStore app** kholo → **+** dabao → `HarshRun-unsigned.ipa` select karo → install.
5. Ho gaya — home screen pe **Harsh Run** (heart icon) aa jayega. Game wahi hai: Easy/Hard, din-raat,
   sorry button, secret warp, best score. iPhone pe character ki awaaz bhi bol sakti hai (iOS support karta hai).

## 7 din wali baat
Free Apple ID ki limit hai — app 7 din baad expire hoti hai.
AltServer PC pe chal raha ho aur phone-PC ek Wi-Fi pe hon to wo khud refresh kar deta hai.
Agar expire ho jaye to AltStore se dobara install kar lo, 2 minute ka kaam hai.

## Agar Codemagic fail ho jaye
- Pehle build me `pod install` / signing error aaye to mujhe bata — `codemagic.yaml` me fix kar dunga.
- Dusra option: **MacinCloud** (rent pe Mac, ~$1/hour) — wahan Xcode khol ke ye project build kar lo.
- Teesra option (paid): median.co jaise services URL se IPA bana deti hain, par paise lagte hain.

## Game update karna ho to
`www/index.html` ko nayi game file se replace karo, phir GitHub Desktop se commit+push karo,
Codemagic pe dobara build dabao — naya IPA aa jayega.
