# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

1000Banks is a React Native fintech application focused on financial freedom, entrepreneurship education, and community building. Built with Expo (v53) and React Native 0.79.5, the app combines e-commerce, educational content, and financial services.

**Core Technologies:**
- **React Native 0.79.5** with **React 19.0.0**
- **Expo Router** for file-based routing
- **TypeScript** with strict mode enabled
- **Firebase Authentication** for user management
- **React Native Firebase** for backend services

## Development Commands

### Core Development
- `npm install` - Install dependencies
- `npm start` or `npx expo start` - Start development server with dev client
- `npm run android` - Run on Android
- `npm run ios` - Run on iOS  
- `npm run web` - Run in web browser
- `npm run lint` - Run ESLint

### Project Management
- `npm run reset-project` - Reset to blank app structure (moves starter code to app-example/)

## Architecture

### Navigation Structure
The app uses a **tab-based navigation** system with the following main sections:
- **Home** (default): Hero content, founder quotes, video section, academy info
- **Courses**: Educational content (placeholder - coming soon)
- **Shop**: Full merchandise store with product grid
- **Trading**: Financial trading features (placeholder - coming soon)
- **Settings**: App configuration (placeholder - coming soon)

Additional navigation includes:
- **Hamburger menu** with: About Us, Services, Buy Merch, We're Hiring, Contact Us
- **Authentication flow** via Sign In/Sign Up buttons

### State Management
- **Tab state**: Managed locally in index.tsx with `activeTab` state
- **Menu state**: Hamburger menu visibility controlled by `menuOpen` state
- **Authentication**: Firebase Auth handles user session state

### Key Components Architecture
- **app/index.tsx**: Main app entry with tab navigation logic and content rendering
- **app/auth.tsx**: Authentication screen with Firebase email/password integration
- **components/SplashScreen.tsx**: Animated splash screen with brand loading animation

### Firebase Integration
- Authentication configured with email/password providers
- Google Services files present for both iOS (`GoogleService-Info.plist`) and Android (`google-services.json`)
- Uses `@react-native-firebase/app` and `@react-native-firebase/auth`

### Design System Implementation

The app follows a dark-themed fintech design (see `mobile app design.webp` for reference).

**Color Constants (AppColors from constants/Colors.ts):**
```typescript
AppColors.primary           // #F5B800 - Golden yellow for CTAs and branding
AppColors.background.dark   // #000000 - Main background
AppColors.background.card   // #1A1A1A - Card backgrounds
AppColors.text.primary      // #FFFFFF - Primary text
AppColors.text.secondary    // #9CA3AF - Secondary text
AppColors.accent.success    // #10B981 - Positive values
AppColors.accent.error      // #EF4444 - Negative values
```

**Component Styling Patterns:**
- Cards: `backgroundColor: AppColors.background.card, borderRadius: 16-20`
- Primary buttons: `backgroundColor: AppColors.primary, borderRadius: 12-24`
- Secondary buttons: `borderColor: AppColors.primary, backgroundColor: 'transparent'`
- Spacing: Use multiples of 8 (8, 16, 24, 32, 40)

### TypeScript Configuration
- Strict mode enabled
- Path aliases configured: `@/*` maps to project root
- Expo TypeScript base configuration extended

## Platform Configuration

### iOS
- Bundle ID: `com.example.1000banks`
- Supports tablets
- Uses static frameworks via expo-build-properties

### Android
- Package: `com.example.banks1000`
- Edge-to-edge enabled
- Uses new React Native architecture (newArchEnabled: true)

## Content Structure

### Home Tab Content
1. **Hero Section**: "Manifesting Positive Vision" messaging with community CTA
2. **Founder Quote**: Devonne Stokes quote with "BUILD A DOOR" philosophy
3. **Video Section**: Financial content with stylized "BREAKTHROUGH" overlay
4. **Academy Section**: "JOIN OUR ACADEMY" coming soon announcement
5. **Merchandise Preview**: Horizontal scroll of first 4 products

### Shop Tab Content
- Grid layout (2 columns) of merchandise items
- 8 products including hoodies, mugs, caps, journals, etc.
- Each product card shows: emoji icon, name, description, price, "Add to Cart" button

### Key UI Patterns
- **Menu Overlay**: Full-screen modal with dark backdrop
- **Tab Switching**: Instant content change managed by `renderTabContent()`
- **Active Tab Indication**: Golden background tint with `activeTab` state
- **Responsive Grid**: `width: (width - 48) / 2` for shop items