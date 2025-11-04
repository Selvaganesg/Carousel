# Ex05 Image Carousel
## Date:15/10/2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
## ImageCarousel.jsx:
```
import React, { useState, useEffect } from "react";

const ImageCarousel = () => {
  
  const images = [
    "https://media.istockphoto.com/id/1458215547/photo/brown-bear.jpg?s=612x612&w=0&k=20&c=MRQhtNC_-P0llLRwwA3wmbQL6iroSjUla1PmvvEWCZU=",
    "https://images.pexels.com/photos/47547/squirrel-animal-cute-rodents-47547.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500",
    "https://i.pinimg.com/736x/32/b9/77/32b977657fc04f8ae459a66a06d9c81a.jpg"


  ];
  

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000); // Change every 3 seconds
    return () => clearInterval(interval); // Cleanup
  }, []);

  return (
    <div style={styles.carouselContainer}>
      <img
        src={images[currentIndex]}
        alt="carousel"
        style={styles.image}
      />
      <button onClick={prevImage} style={styles.button}>◀</button>
      <button onClick={nextImage} style={styles.button}>▶</button>
      <p style={styles.caption}>{currentIndex + 1} / {images.length}</p>
    </div>
  );
};

const styles = {
  carouselContainer: {
    position: "relative",
    width: "600px",
    height: "400px",
    margin: "auto",
    overflow: "hidden",
    borderRadius: "10px",
    boxShadow: "0 4px 10px rgba(0,0,0,0.3)",
  },
  image: {
    width: "100%",
    height: "100%",
    objectFit: "cover",
  },
  button: {
    position: "absolute",
    top: "50%",
    transform: "translateY(-50%)",
    background: "rgba(255,255,255,0.7)",
    border: "none",
    fontSize: "1.5rem",
    cursor: "pointer",
    padding: "5px 10px",
  },
  caption: {
    position: "absolute",
    bottom: "10px",
    left: "50%",
    transform: "translateX(-50%)",
    color: "white",
    background: "rgba(0,0,0,0.4)",
    padding: "5px 10px",
    borderRadius: "5px",
  },
};


export default ImageCarousel;

```
## App.jsx:
```
import ImageCarousel from "./ImageCarousel";

function App() {
  return (
    <div>
      <h2 ><center>React Image Carousel</center></h2>
      <ImageCarousel />
    </div>
  );
}

export default App;

```
## OUTPUT
<img width="1342" height="915" alt="Screenshot 2025-10-15 083655" src="https://github.com/user-attachments/assets/3394a2f9-6e0e-42e2-8dc1-039cc415ad82" />
<img width="1196" height="932" alt="Screenshot 2025-10-15 083708" src="https://github.com/user-attachments/assets/a3be2845-cc1e-4555-aa2e-4e0d186ffab9" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
