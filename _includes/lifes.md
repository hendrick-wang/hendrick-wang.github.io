## Lives

<div class="photo-gallery">
  <div class="gallery-container">
    <div class="gallery-wrapper">
      <div class="gallery-slide active">
        <img src="./assets/img/image.png" alt="Life Photo 1" />
      </div>
      <div class="gallery-slide">
        <img src="./assets/img/family.jpg" alt="Family Photo" />
      </div>
    </div>
    
    <button class="gallery-nav gallery-prev" onclick="previousSlide()">
      <i class="fas fa-chevron-left"></i>
    </button>
    <button class="gallery-nav gallery-next" onclick="nextSlide()">
      <i class="fas fa-chevron-right"></i>
    </button>
    
    <div class="gallery-dots">
      <span class="dot active" onclick="currentSlide(1)"></span>
      <span class="dot" onclick="currentSlide(2)"></span>
    </div>
  </div>
</div>

<style>
.photo-gallery {
  max-width: 600px;
  margin: 20px auto;
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
}

@media (prefers-color-scheme: dark) {
  .photo-gallery {
    background: rgba(32, 33, 43, 0.95);
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  }
}

.gallery-container {
  position: relative;
  width: 100%;
  overflow: hidden;
}

.gallery-wrapper {
  display: flex;
  transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.gallery-slide {
  min-width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f8f9fa;
}

@media (prefers-color-scheme: dark) {
  .gallery-slide {
    background: #2a2d3a;
  }
}

.gallery-slide img {
  width: 100%;
  height: 400px;
  object-fit: cover;
  display: block;
  transition: transform 0.3s ease;
}

.gallery-slide img:hover {
  transform: scale(1.02);
}

.gallery-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.9);
  border: none;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  font-size: 16px;
  color: #333;
  transition: all 0.3s ease;
  z-index: 10;
  backdrop-filter: blur(10px);
}

@media (prefers-color-scheme: dark) {
  .gallery-nav {
    background: rgba(32, 33, 43, 0.9);
    color: #e2e8f0;
  }
}

.gallery-nav:hover {
  background: rgba(255, 255, 255, 1);
  transform: translateY(-50%) scale(1.1);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

@media (prefers-color-scheme: dark) {
  .gallery-nav:hover {
    background: rgba(32, 33, 43, 1);
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
  }
}

.gallery-prev {
  left: 15px;
}

.gallery-next {
  right: 15px;
}

.gallery-dots {
  display: flex;
  justify-content: center;
  padding: 20px;
  gap: 12px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.3);
  cursor: pointer;
  transition: all 0.3s ease;
}

@media (prefers-color-scheme: dark) {
  .dot {
    background: rgba(255, 255, 255, 0.3);
  }
}

.dot.active,
.dot:hover {
  background: #007bff;
  transform: scale(1.2);
}

@media (prefers-color-scheme: dark) {
  .dot.active,
  .dot:hover {
    background: #3eb7f0;
  }
}

@media (max-width: 768px) {
  .photo-gallery {
    margin: 15px;
    border-radius: 8px;
  }
  
  .gallery-slide img {
    height: 280px;
  }
  
  .gallery-nav {
    width: 35px;
    height: 35px;
    font-size: 14px;
  }
  
  .gallery-prev {
    left: 10px;
  }
  
  .gallery-next {
    right: 10px;
  }
}
</style>

<script>
let currentSlideIndex = 0;
const slides = document.querySelectorAll('.gallery-slide');
const dots = document.querySelectorAll('.dot');
const totalSlides = slides.length;

function showSlide(index) {
  const wrapper = document.querySelector('.gallery-wrapper');
  const offset = -index * 100;
  wrapper.style.transform = `translateX(${offset}%)`;
  
  // Update active states
  slides.forEach((slide, i) => {
    slide.classList.toggle('active', i === index);
  });
  
  dots.forEach((dot, i) => {
    dot.classList.toggle('active', i === index);
  });
  
  currentSlideIndex = index;
}

function nextSlide() {
  const nextIndex = (currentSlideIndex + 1) % totalSlides;
  showSlide(nextIndex);
}

function previousSlide() {
  const prevIndex = (currentSlideIndex - 1 + totalSlides) % totalSlides;
  showSlide(prevIndex);
}

function currentSlide(index) {
  showSlide(index - 1);
}

// Touch/swipe support for mobile
let startX = 0;
let currentX = 0;
let isDragging = false;

const galleryContainer = document.querySelector('.gallery-container');

galleryContainer.addEventListener('touchstart', (e) => {
  startX = e.touches[0].clientX;
  isDragging = true;
});

galleryContainer.addEventListener('touchmove', (e) => {
  if (!isDragging) return;
  currentX = e.touches[0].clientX;
});

galleryContainer.addEventListener('touchend', () => {
  if (!isDragging) return;
  
  const diff = startX - currentX;
  const threshold = 50;
  
  if (Math.abs(diff) > threshold) {
    if (diff > 0) {
      nextSlide();
    } else {
      previousSlide();
    }
  }
  
  isDragging = false;
});

// Keyboard navigation
document.addEventListener('keydown', (e) => {
  if (e.key === 'ArrowLeft') {
    previousSlide();
  } else if (e.key === 'ArrowRight') {
    nextSlide();
  }
});

// Auto-play (optional, uncomment to enable)
// setInterval(nextSlide, 5000);
</script>

