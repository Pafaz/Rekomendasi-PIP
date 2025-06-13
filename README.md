# 🖥️ Frontend SPK PIP – Next.js  
Frontend aplikasi SPK PIP menggunakan Next.js 15, MUI, Tailwind CSS, dan autentikasi JWT yang terhubung ke backend API berbasis Hapi.js.  
## ⚙️ Teknologi  
- [Next.js 15](https://nextjs.org/)  
- [React 19](https://react.dev/)  
- [MUI 7](https://mui.com/)  
- [Tailwind CSS 4](https://tailwindcss.com/)  
- [JWT](https://jwt.io/) + [js-cookie](https://github.com/js-cookie/js-cookie)  
- [Recharts](https://recharts.org/), [SweetAlert2](https://sweetalert2.github.io/), dan [PDF Generator (jsPDF/html2pdf)]  
## 📁 Struktur Folder  
```
.  
├── pages/  
│   ├── index.js  
│   ├── login.js  
│   ├── dashboard/  
│   └── _middleware.js  
├── components/  
├── services/  
├── utils/  
├── styles/  
├── .env.local  
├── package.json  
└── README.md  
```  
## 🌐 Environment Variable (.env.local)  
```env  
NEXT_PUBLIC_API_URL=http://localhost:5000  
NEXT_PUBLIC_JWT_SECRET=isi_secret_jwt_mu  
```  
## 🛠️ Instalasi  
```bash  
git clone https://github.com/username/my-pip-frontend.git  
cd my-pip-frontend  
npm install  
```  
## ▶️ Menjalankan Aplikasi  
```bash  
npm run dev  
```  
## 🔐 Autentikasi  
- Login → simpan JWT di cookie dengan [js-cookie]  
- Middleware di `pages/_middleware.js` akan mengecek token  
- Jika tidak valid → redirect ke `/login`  
Contoh:  
```js  
import { NextResponse } from 'next/server'  
import jwt from 'jsonwebtoken'  
export function middleware(req) {  
  const token = req.cookies.get('token')  
  try {  
    jwt.verify(token?.value, process.env.NEXT_PUBLIC_JWT_SECRET)  
    return NextResponse.next()  
  } catch (err) {  
    return NextResponse.redirect(new URL('/login', req.url))  
  }  
}  
```  
## 📦 API Komunikasi  
Menggunakan `axios` (bisa ditambahkan manual):  
```bash  
npm install axios  
```  
Contoh:  
```js  
import axios from 'axios'  
const api = axios.create({ baseURL: process.env.NEXT_PUBLIC_API_URL })  
export default api  
```  
## ✅ Fitur  
- Login & proteksi halaman menggunakan JWT  
- CRUD siswa, hasil, dan rekap  
- Dashboard visualisasi menggunakan Recharts  
- Export data ke PDF (jsPDF, html2pdf, react-to-print)  
- SweetAlert2 untuk konfirmasi  
- Kompatibel dengan TensorFlow.js (opsional)  
## 📦 Script yang Tersedia  
- `npm run dev` – Jalankan development server  
- `npm run build` – Build production  
- `npm run start` – Jalankan build hasil produksi  
- `npm run export` – Export static HTML  
- `npm run lint` – Cek kualitas kode  
## 📝 Lisensi  
Proyek ini menggunakan lisensi [MIT](LICENSE)  
