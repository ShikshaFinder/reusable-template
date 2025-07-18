# SaaS Boilerplate

A production-ready SaaS website starter built with Next.js 14+, Prisma, TailwindCSS, and NextAuth.js.

## 🚀 Features

- **Next.js 14+** with App Router
- **TailwindCSS** for styling
- **Prisma ORM** with PostgreSQL
- **NextAuth.js** for authentication
- **Role-based access control** (Admin only)
- **Azure Blob Storage** integration (ready to implement)
- **Database connection pooling** support
- **TypeScript** support
- **Responsive design**

## 📦 Tech Stack

- **Frontend**: Next.js 14+, React 19, TailwindCSS
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL with Prisma ORM
- **Authentication**: NextAuth.js
- **Styling**: TailwindCSS
- **Language**: TypeScript

## 🛠️ Setup Instructions

### 1. Clone and Install Dependencies

```bash
git clone <your-repo-url>
cd reuse
npm install
```

### 2. Environment Setup

1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Update your `.env` file with your configuration:
```env
DATABASE_URL=postgresql://USER:PASSWORD@HOST:PORT/DATABASE
NEXTAUTH_SECRET=your-super-secret-key
NEXTAUTH_URL=http://localhost:3000
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD_HASH=your-hashed-password
```

3. Generate a password hash for the admin user:
```bash
node scripts/generate-password.js your-admin-password
```

### 3. Database Setup

1. Set up your PostgreSQL database
2. Run Prisma migrations:
```bash
npx prisma migrate dev --name init
```

3. Generate Prisma client:
```bash
npx prisma generate
```

### 4. Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to see the application.

## 🔐 Authentication

### Admin Login
- Only one admin user is allowed (configured via environment variables)
- Admin credentials are stored in `.env`:
  - `ADMIN_EMAIL`: Admin email address
  - `ADMIN_PASSWORD_HASH`: Hashed admin password

### Role-based Access
- Admin users can access `/dashboard`
- Regular users are redirected to home page
- Unauthenticated users are redirected to `/login`

## 📁 Project Structure

```
├── app/
│   ├── api/
│   │   ├── auth/           # NextAuth handlers
│   │   └── upload/         # Azure blob upload endpoint
│   ├── dashboard/          # Admin-only area
│   ├── login/              # Login page
│   └── page.tsx            # Home page
├── components/
│   ├── AuthForm.tsx        # Authentication form
│   ├── ImageUploader.tsx   # Image upload component
│   └── Navbar.tsx          # Navigation component
├── lib/
│   ├── auth.ts             # Auth helper functions
│   ├── auth-context.tsx    # Auth context provider
│   ├── db.ts               # Prisma client setup
│   └── azure.ts            # Azure blob storage helpers
├── prisma/
│   └── schema.prisma       # Database schema
└── scripts/
    └── generate-password.js # Password hash generator
```

## 🔧 Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | PostgreSQL connection string | Yes |
| `NEXTAUTH_SECRET` | NextAuth secret key | Yes |
| `NEXTAUTH_URL` | Application URL | Yes |
| `ADMIN_EMAIL` | Admin user email | Yes |
| `ADMIN_PASSWORD_HASH` | Hashed admin password | Yes |
| `GOOGLE_CLIENT_ID` | Google OAuth client ID | No |
| `GOOGLE_CLIENT_SECRET` | Google OAuth client secret | No |
| `AZURE_STORAGE_ACCOUNT_NAME` | Azure storage account name | No |
| `AZURE_STORAGE_ACCOUNT_KEY` | Azure storage account key | No |
| `AZURE_BLOB_CONTAINER_NAME` | Azure blob container name | No |

### Optional Features

#### Google OAuth
To enable Google OAuth:
1. Set up a Google OAuth application
2. Add `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` to your `.env`

#### Azure Blob Storage
To enable Azure Blob Storage:
1. Set up an Azure Storage account
2. Add Azure storage variables to your `.env`
3. Implement the upload functionality in `lib/azure.ts`

## 🚀 Deployment

### Vercel (Recommended)
1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

### Other Platforms
The application can be deployed to any platform that supports Next.js:
- Netlify
- Railway
- DigitalOcean App Platform
- AWS Amplify

## 📝 Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

If you encounter any issues or have questions, please open an issue on GitHub.
