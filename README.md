# 🎵 Spotify-Like Music Streaming App

A full-stack music streaming web application inspired by Spotify. The project provides a responsive music-listening interface, a backend REST API for managing songs and albums, and a dedicated admin dashboard for uploading and managing music content.

## ✨ Features

### 🎧 Music Player

* Play and pause songs
* Next and previous track controls
* Select and play individual songs
* Seek through the current track
* Real-time playback progress and duration
* Audio playback using the browser's HTML5 Audio API

### 📀 Music & Album Management

* Fetch songs and albums from the backend
* Display music content through reusable React components
* Store song metadata including name, description, album, image, audio file, and duration
* Store album information including name, description, background color, and artwork

### 🛠️ Admin Dashboard

* Add new songs
* Upload song audio and artwork
* Add new albums
* View existing songs and albums
* Remove songs and albums
* Dedicated admin interface built with React and React Router

### ☁️ Media Storage

* Audio and image uploads handled using **Multer**
* Media files uploaded to **Cloudinary**
* Cloudinary URLs stored with the corresponding song/album data

### 📱 Responsive UI

* Spotify-inspired dark interface
* Responsive layout for different screen sizes
* Reusable React components for songs, albums, navigation, and player controls

---

## 🏗️ Architecture

```text
                    ┌─────────────────────┐
                    │    Music Client     │
                    │ React + Vite        │
                    │ Tailwind CSS        │
                    └──────────┬──────────┘
                               │
                             Axios
                               │
                               ▼
                    ┌─────────────────────┐
                    │      Backend        │
                    │ Node.js + Express   │
                    │ REST API            │
                    └───────┬─────┬───────┘
                            │     │
                            │     └────────────────┐
                            ▼                      ▼
                    ┌───────────────┐      ┌───────────────┐
                    │   MongoDB     │      │   Cloudinary  │
                    │ Song/Album    │      │ Audio/Images  │
                    │ Metadata      │      │ Media Storage │
                    └───────────────┘      └───────────────┘
                            ▲
                            │
                    ┌───────┴────────┐
                    │  Admin Panel   │
                    │ React + Vite   │
                    │ Song/Album Mgmt│
                    └────────────────┘
```

---

## 🧰 Tech Stack

### Frontend

* React.js
* Vite
* JavaScript
* Tailwind CSS
* React Router
* Axios
* HTML5 Audio API

### Backend

* Node.js
* Express.js
* MongoDB
* Mongoose
* Multer
* Cloudinary
* CORS
* dotenv

### Admin Panel

* React.js
* Vite
* React Router
* Axios
* Tailwind CSS
* React Toastify

---

## 📂 Project Structure

```text
Spotify-clone/
│
├── Music main/                 # Music streaming client
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   │   ├── AlbumItem.jsx
│   │   │   ├── Display.jsx
│   │   │   ├── DisplayAlbum.jsx
│   │   │   ├── DisplayHome.jsx
│   │   │   ├── Navbar.jsx
│   │   │   ├── Player.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   └── SongItem.jsx
│   │   ├── context/
│   │   │   └── PlayerContext.jsx
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
│
├── backend/                   # Express REST API
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   │   ├── albumController.js
│   │   │   └── songController.js
│   │   ├── middleware/
│   │   ├── models/
│   │   │   ├── albumModel.js
│   │   │   └── songModel.js
│   │   └── routes/
│   │       ├── albumRoute.js
│   │       └── songRoute.js
│   ├── server.js
│   └── package.json
│
├── admin/                    # Admin dashboard
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

* [Node.js](https://nodejs.org/)
* npm
* MongoDB database
* Cloudinary account

### 1. Clone the Repository

```bash
git clone https://github.com/Yuvraj-Kathad/Spotify-clone.git
cd Spotify-clone
```

### 2. Setup the Backend

```bash
cd backend
npm install
```

Create a `.env` file inside the `backend` directory:

```env
PORT=4000
MONGO_DB_URI=your_mongodb_connection_string
CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

Start the backend:

```bash
npm start
```

For development with Nodemon:

```bash
npm run server
```

The backend runs by default on:

```text
http://localhost:4000
```

---

### 3. Setup the Music Client

Open another terminal:

```bash
cd "Music main"
npm install
npm run dev
```

Vite will provide the local development URL in the terminal.

---

### 4. Setup the Admin Panel

Open another terminal:

```bash
cd admin
npm install
npm run dev
```

Open the local URL provided by Vite in your browser.

---

## 🔌 API Endpoints

### Songs

| Method | Endpoint            | Description                         |
| ------ | ------------------- | ----------------------------------- |
| `POST` | `/api/songs/add`    | Add a new song with image and audio |
| `GET`  | `/api/songs/list`   | Fetch all songs                     |
| `POST` | `/api/songs/remove` | Remove a song                       |

### Albums

| Method | Endpoint             | Description      |
| ------ | -------------------- | ---------------- |
| `POST` | `/api/albums/add`    | Add a new album  |
| `GET`  | `/api/albums/list`   | Fetch all albums |
| `POST` | `/api/albums/remove` | Remove an album  |

The backend separates routes, controllers, models, and middleware to keep the API modular and easier to maintain.

---

## 🎮 How It Works

1. The admin uploads songs or albums through the admin dashboard.
2. Uploaded audio and images are processed by the backend.
3. Media files are stored using Cloudinary.
4. Song and album metadata is stored in MongoDB.
5. The React music client requests songs and albums through the REST API.
6. The player stores the selected track and playback state using React Context.
7. The browser's HTML5 Audio API handles actual audio playback.

---

## 🧠 Key Implementation Details

### React Context for Player State

`PlayerContext` centralizes the application's music-player state, including:

* Current track
* Playback status
* Current and total duration
* Song and album data
* Audio element reference
* Play/pause functionality
* Next/previous navigation
* Track seeking

This allows different components such as the sidebar, song cards, and player to share the same playback state.

### REST API

The backend exposes separate song and album routes and controllers. Mongoose models are used to define and persist song and album metadata in MongoDB.

### Cloudinary Integration

Audio files and album artwork are uploaded to Cloudinary, while the returned secure URLs are stored in the database for later playback and display.

---

## 📸 Screenshots

Add screenshots of the following interfaces to make the repository easier to understand:

```text
screenshots/
├── home.png
├── album.png
├── music-player.png
└── admin-dashboard.png
```

Then reference them in this README:

```markdown
![Home](screenshots/home.png)
![Music Player](screenshots/music-player.png)
![Admin Dashboard](screenshots/admin-dashboard.png)
```

---

## 🔮 Future Improvements

* User authentication and authorization
* User-specific playlists
* Like/favorite songs
* Search functionality
* Recently played tracks
* Personalized recommendations
* Better error handling and loading states
* Production deployment configuration
* Protected admin routes
* Pagination for large music libraries
* Improved API validation and security

---

## 📚 Learning Outcomes

This project provided hands-on experience with:

* Full-stack web application development
* React component architecture
* React Context for state management
* REST API design
* Express.js backend development
* MongoDB and Mongoose
* File upload handling with Multer
* Cloudinary media storage
* Admin dashboard development
* Browser-based audio playback
* Frontend-backend integration using Axios

---

## 👨‍💻 Author

**Yuvraj Kathad**

GitHub:
https://github.com/Yuvraj-Kathad

Project Repository:
https://github.com/Yuvraj-Kathad/Spotify-clone

---

## 📄 License

This project is open source and available under the MIT License.
