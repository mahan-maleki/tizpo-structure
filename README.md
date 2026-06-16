# Tizpo Front-End Folder Structure

in Tizpo Web App, We have three services like:

- Seller Panel
- Store
- Admin Panel/Affiliate Panel

we should to have three source codes for theese apps.

I suggest this structure at All:

1.  «app» folder for Web Application source
2.  «components» folder for Website Section Components
3.  «features» folder for "Feature-Sliced" design
4.  «lib» folder for getting datas from 'backend'
5.  «public» folder for static files like "images" and "fonts"

---

### App Folder

in this folder, we should to develop pages, import components and use it like UI design.
for example, in seller panel we should to have "auth","dashboard" and "globals.css" file;
in 'auth' and other app childs we have:

- page.ts
- layout.ts
- OTHER ROUTES

### Components Folder

in this folder we have some other folders that bring every section of website components.
for example, in seller panel, we have a components folder that brings "ui", "layout" and "common" folders.

- #### UI: this folder brings components that are related to ui components like "button", "inputs" .etc
- #### Layout: this folder brings components that are related to layouts components like "logo image" "menu items" .etc
- #### Common: this folder brings components that are very useful and popular in project

### Features Folder

in this folder we should to develop features like "products" and "orders" components.

### Lib Folder

in this folder, we should to get datas from backend services (API's) to client side.
for example we have "api.ts" file in this folder that gets related api from backend.

### Public Folder

in this folder, we should to upload and use static files like "images", "fonts" and other static files.
for example we should to upload the brand logo in this folder, because we can use it easier in development.

---

## Structures

in this section of document, we'll review the sample structure that I suggested for using in development.

### Seller Panel

`tizpoo-seller-panel/`

├── app/ # App Router  
│ ├── (auth)/  
│ ├── (dashboard)/  
│ │ ├── layout.tsx  
│ │ ├── products/  
│ │ ├── orders/  
│ │ ├── analytics/  
│ │ └── settings/  
│ └── globals.css  
├── components/  
│ ├── ui/ # کامپوننت‌های محلی  
│ ├── layout/  
│ └── common/  
├── features/ # Feature-Sliced Design  
│ ├── products/  
│ ├── orders/  
│ └── ...  
├── lib/  
│ ├── api.ts # Client برای فراخوانی Backend  
│ ├── utils.ts  
│ └── auth.ts  
├── hooks/  
├── types/  
├── public/  
├── next.config.ts  
├── tailwind.config.ts  
├── tsconfig.json  
├── package.json  
└── .env.local

### Store Structure

`tizpoo-store/`

├── app/  
│ ├── (shop)/  
│ ├── products/  
│ ├── cart/  
│ ├── checkout/  
│ └── category/[slug]/  
├── components/  
├── features/  
├── lib/api.ts  
├── next.config.ts  
├── tailwind.config.ts  
└── ...

### Admin Panel

`tizpoo-admin/  `

├── app/  
│ ├── (admin)/  
│ │ ├── users/  
│ │ ├── sellers/  
│ │ ├── transactions/  
│ │ └── ...  
├── components/  
├── features/  
└── ...
