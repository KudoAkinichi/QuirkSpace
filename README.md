# QuirkSpace - Social Media Application

QuirkSpace is a modern social media application built with React, TypeScript, and Appwrite. It provides a feature-rich platform for users to share posts, interact with others, and manage their social presence.

## 🚀 Core Features

### 1. Authentication System

- Secure email/password authentication using Appwrite
- Protected routes and auth state management
- User session handling
- Signup and Signin forms with validation

```js
// Example of protected route handling
const AuthLayout = () => {
  const isAuthenticated = false;
  return (
    <>
      {isAuthenticated ? (
        <Navigate to="/" />
      ) : (
        // Auth forms layout
      )}
    </>
  );
};
```

### 2. Post Management

- Create, read, update, and delete posts
- Image upload support
- Location tagging
- Post caption with hashtags
- Rich post details view
- Like and save functionality

```js
// Example of post creation
export async function createPost(post: INewPost) {
  try {
    const uploadedFile = await uploadFile(post.file[0]);
    const fileUrl = await getFileView(uploadedFile.$id);
    const tags = post.tags?.replace(/ /g, "").split(",") || [];
    
    const newPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      ID.unique(),
      {
        creator: post.userId,
        caption: post.caption,
        imageUrl: fileUrl,
        imageId: uploadedFile.$id,
        location: post.location,
        tags: tags,
      }
    );
    return newPost;
  } catch (error) {
    console.log(error);
  }
}
```

### 3. User Profiles

- Customizable user profiles
- Profile picture upload
- Bio and personal information
- User posts grid view
- Liked posts section
- Following/Followers system

### 4. Social Features

- Home feed with recent posts
- Explore page with infinite scroll
- Post interactions (likes, saves)
- User search functionality
- Top creators section

### 5. UI/UX Features

- Responsive design (mobile-first approach)
- Dark theme
- Modern UI components using shadcn/ui
- Loading states and animations
- Toast notifications
- Form validations using Zod

## 🛠️ Setup & Configuration

Before getting started make sure to make an account in appwrite and set the schema in appwrite with exact name as in application to make it work.

1. Create a `.env.local` file with this format:

```env
VITE_APPWRITE_PROJECT_ID=
VITE_APPWRITE_URL=
VITE_APPWRITE_STORAGE_ID=
VITE_APPWRITE_DATABASE_ID=
VITE_APPWRITE_USER_COLLECTION_ID=
VITE_APPWRITE_POST_COLLECTION_ID=
VITE_APPWRITE_SAVES_COLLECTION_ID=
```

2. Run the following commands to get started:

```bash
npm install
npm run dev
```

## 📂 Project Structure

```
src/
  ├── _auth/          # Authentication related components
  ├── _root/          # Main application routes
  ├── components/     # Reusable components
  ├── constants/      # Constants and configurations
  ├── context/        # React context providers
  ├── hooks/          # Custom hooks
  ├── lib/           # Utility functions and API
  └── types/         # TypeScript type definitions
```

## 🔧 Technical Implementation

### State Management

- React Query for server state management
- Context API for auth state
- Optimistic updates for better UX

```js
// Query hook example
export const useGetRecentPosts = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
    queryFn: getRecentPosts,
  });
};
```

### Backend Integration

- Appwrite as Backend-as-a-Service
- Custom API wrapper for Appwrite services
- File storage for images
- Real-time database updates

### Performance Optimizations

- Image optimization
- Lazy loading components
- Debounced search
- Infinite scroll implementation

```js
// Debounce hook implementation
export default function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value);
  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);
    return () => clearTimeout(handler);
  }, [value, delay]);
  return debouncedValue;
}
```

### React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

### Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
   parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
   },
```

- Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
- Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list

## 🎨 Styling

- TailwindCSS for styling
- Custom utility classes
- Responsive design patterns
- Consistent theme variables

## 🔐 Security Features

- Input validation using Zod
- Protected API routes
- Secure file upload handling
- Session management
- XSS prevention

## 🌟 Advanced Features

1. Infinite Scroll
2. Real-time updates
3. Image optimization
4. Search functionality
5. Social interactions

## 📱 Responsive Design

- Mobile-first approach
- Breakpoint system
- Adaptive layouts
- Touch-friendly interfaces

## 🧪 Future Enhancements

1. Real-time messaging
2. Push notifications
3. Video support
4. Enhanced analytics
5. Community features
6. Multiple image uploads
