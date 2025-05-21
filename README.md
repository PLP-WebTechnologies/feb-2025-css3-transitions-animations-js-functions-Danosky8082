# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

Answer

index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>CSS Animation + localStorage Example</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <button id="animateBtn">Click me to Animate</button>

  <script src="script.js"></script>
</body>
</html>

styles.css

/* Button styling */
#animateBtn {
  padding: 15px 30px;
  font-size: 18px;
  background-color: #4caf50;
  border: none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

/* Change background on hover */
#animateBtn:hover {
  background-color: #45a049;
}

/* Define keyframes for animation */
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-30px);
  }
}

/* Animation class to trigger bounce */
.bounce {
  animation: bounce 0.6s ease;
}


script.js

const btn = document.getElementById('animateBtn');

// Function to add animation class and store state in localStorage
function animateButton() {
  // Add animation class
  btn.classList.add('bounce');

  // Store that animation was triggered
  localStorage.setItem('buttonAnimated', 'true');

  // Remove animation class after animation ends (to allow re-trigger)
  btn.addEventListener('animationend', () => {
    btn.classList.remove('bounce');
  }, { once: true });
}

// Retrieve animation state from localStorage on page load
window.addEventListener('DOMContentLoaded', () => {
  const animated = localStorage.getItem('buttonAnimated');

  if (animated === 'true') {
    // Optionally trigger animation or change style on load
    btn.style.backgroundColor = '#2e7d32'; // Darker green to indicate stored preference
  }
});

// Add click event to button
btn.addEventListener('click', animateButton);
