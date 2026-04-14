# 📍 React Custom Hook – useGeolocation

## 🚀 Overview

This project demonstrates how to build and use a **custom React hook** called `useGeolocation` to fetch the user’s current GPS location using the browser’s Geolocation API.

It showcases:

* Custom hook creation
* State management using React Hooks
* Handling asynchronous browser APIs
* Error handling and loading states

---

## 🧠 What is `useGeolocation`?

`useGeolocation` is a reusable custom hook that:

* Fetches the user's current latitude and longitude
* Tracks loading state while fetching location
* Handles errors (e.g., permission denied, unsupported browser)

---

## ⚙️ Features

* 📍 Get real-time user location (latitude & longitude)
* ⏳ Loading indicator while fetching data
* ❌ Graceful error handling
* 🔁 Tracks number of location requests
* 🔗 Direct link to OpenStreetMap for visualization

---

## 🏗️ Project Structure

```
.
├── App.js
├── useGeolocation (custom hook inside App.js)
└── README.md
```

---

## 🔧 How It Works

### 1. Custom Hook Logic

The hook uses:

* `useState` for managing:

  * `isLoading`
  * `position`
  * `error`
* `navigator.geolocation.getCurrentPosition()` to fetch location

---

### 2. API Flow

1. User clicks **"Get my position"**
2. Hook triggers geolocation request
3. Browser asks for permission
4. On success:

   * Latitude & longitude are stored
5. On failure:

   * Error message is displayed

---

## 🧩 Code Example (Core Hook)

```js
function useGeolocation() {
  const [isLoading, setIsLoading] = useState(false);
  const [position, setPosition] = useState({});
  const [error, setError] = useState(null);

  function getPosition() {
    if (!navigator.geolocation)
      return setError("Your browser does not support geolocation");

    setIsLoading(true);

    navigator.geolocation.getCurrentPosition(
      (pos) => {
        setPosition({
          lat: pos.coords.latitude,
          lng: pos.coords.longitude,
        });
        setIsLoading(false);
      },
      (error) => {
        setError(error.message);
        setIsLoading(false);
      }
    );
  }

  return { isLoading, position, error, getPosition };
}
```

---

## 🖥️ UI Behavior

* Button triggers location fetch
* Displays:

  * Loading state
  * Error message (if any)
  * Latitude & longitude (with map link)
* Tracks how many times user requested location

---

## 🔗 Example Output

```
Your GPS position: 16.5062, 80.6480
```

(Clickable link opens location in OpenStreetMap)

---

## 📚 Concepts Covered

* Custom React Hooks
* `useState`
* Asynchronous JavaScript
* Browser APIs (Geolocation)
* Conditional rendering
* Clean separation of logic and UI

---

## ⚠️ Important Notes

* Requires user permission for location access
* Works only in secure contexts (HTTPS)
* May not work in older browsers

---

## 🚀 Future Improvements

* Add `useEffect` to auto-fetch location
* Add caching of last location
* Add map preview (Google Maps / Leaflet)
* Add debounce/throttle for repeated clicks

---

## 🎯 Learning Outcome

After this project, you should understand:

* How to create reusable logic using custom hooks
* How to handle real-world async operations in React
* How to separate concerns between UI and logic

---

## 👨‍💻 Author
Surya Teja Tangella

Built as part of React learning journey focusing on:

* Hooks
* Real-world APIs
* Clean architecture

---
