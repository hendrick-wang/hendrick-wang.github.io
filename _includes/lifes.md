## Lives

<div class="elegant-gallery">
  <div class="gallery-viewport">
    <div class="slides-container">
      <div class="slide active" data-index="0">
        <div class="image-frame">
          <img src="./assets/img/image.png" alt="Life Photo 1" loading="lazy" />
          <div class="image-overlay"></div>
        </div>
      </div>
      <div class="slide" data-index="1">
        <div class="image-frame">
          <img src="./assets/img/family.jpg" alt="Family Photo" loading="lazy" />
          <div class="image-overlay"></div>
        </div>
      </div>
    </div>
    
    <nav class="gallery-controls">
      <button class="nav-btn prev-btn" onclick="navigateSlide(-1)" aria-label="Previous image">
        <svg viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
          <path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"/>
        </svg>
      </button>
      <button class="nav-btn next-btn" onclick="navigateSlide(1)" aria-label="Next image">
        <svg viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
          <path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/>
        </svg>
      </button>
    </nav>
  </div>
</div>

<style>
.elegant-gallery {
  max-width: 300px;
  margin: 30px auto;
  position: relative;
  border-radius: 16px;
  overflow: hidden;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  border: 1px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(20px);
  box-shadow: 
    0 16px 40px rgba(0, 0, 0, 0.12),
    0 8px 16px rgba(0, 0, 0, 0.08),
    inset 0 1px 0 rgba(255, 255, 255, 0.15);
  transition: all 0.3s ease;
}

@media (prefers-color-scheme: dark) {
  .elegant-gallery {
    background: linear-gradient(135deg, rgba(32, 33, 43, 0.95), rgba(24, 25, 31, 0.9));
    border: 1px solid rgba(255, 255, 255, 0.1);
    box-shadow: 
      0 16px 40px rgba(0, 0, 0, 0.4),
      0 8px 16px rgba(0, 0, 0, 0.3),
      inset 0 1px 0 rgba(255, 255, 255, 0.1);
  }
}

.elegant-gallery:hover {
  transform: translateY(-2px);
  box-shadow: 
    0 20px 50px rgba(0, 0, 0, 0.15),
    0 12px 20px rgba(0, 0, 0, 0.1),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
}

@media (prefers-color-scheme: dark) {
  .elegant-gallery:hover {
    box-shadow: 
      0 20px 50px rgba(0, 0, 0, 0.5),
      0 12px 20px rgba(0, 0, 0, 0.4),
      inset 0 1px 0 rgba(255, 255, 255, 0.15);
  }
}

.gallery-viewport {
  position: relative;
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.slides-container {
  display: flex;
  width: 200%;
  height: 100%;
  transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.slide {
  width: 50%;
  height: 100%;
  position: relative;
  opacity: 0.7;
  transition: opacity 0.6s ease;
}

.slide.active {
  opacity: 1;
}

.image-frame {
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
}

.image-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  filter: contrast(1.05) saturate(1.1);
}

.slide.active .image-frame img {
  transform: scale(1.02);
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 0.1) 100%
  );
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}

.slide:hover .image-overlay {
  opacity: 1;
}

.gallery-controls {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 8px;
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.elegant-gallery:hover .gallery-controls {
  opacity: 1;
  pointer-events: all;
}

.nav-btn {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95), rgba(255, 255, 255, 0.85));
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(15px);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 
    0 4px 12px rgba(0, 0, 0, 0.1),
    inset 0 1px 0 rgba(255, 255, 255, 0.4);
}

@media (prefers-color-scheme: dark) {
  .nav-btn {
    background: linear-gradient(135deg, rgba(45, 47, 60, 0.95), rgba(35, 37, 48, 0.9));
    border: 1px solid rgba(255, 255, 255, 0.15);
    color: rgba(255, 255, 255, 0.9);
    box-shadow: 
      0 4px 12px rgba(0, 0, 0, 0.3),
      inset 0 1px 0 rgba(255, 255, 255, 0.1);
  }
}

.nav-btn:hover {
  transform: scale(1.15);
  background: linear-gradient(135deg, rgba(255, 255, 255, 1), rgba(248, 249, 250, 0.95));
  box-shadow: 
    0 6px 20px rgba(0, 0, 0, 0.15),
    inset 0 1px 0 rgba(255, 255, 255, 0.6);
}

@media (prefers-color-scheme: dark) {
  .nav-btn:hover {
    background: linear-gradient(135deg, rgba(55, 57, 70, 0.98), rgba(45, 47, 60, 0.95));
    box-shadow: 
      0 6px 20px rgba(0, 0, 0, 0.4),
      inset 0 1px 0 rgba(255, 255, 255, 0.2);
  }
}

.nav-btn:active {
  transform: scale(1.05);
}

.nav-btn svg {
  transition: transform 0.2s ease;
}

.nav-btn:hover svg {
  transform: scale(1.1);
}

@media (max-width: 768px) {
  .elegant-gallery {
    max-width: 250px;
    margin: 20px auto;
    border-radius: 12px;
  }
  
  .gallery-viewport {
    height: 160px;
  }
  
  .nav-btn {
    width: 30px;
    height: 30px;
  }
  
  .nav-btn svg {
    width: 16px;
    height: 16px;
  }
  
  .gallery-controls {
    padding: 0 6px;
  }
}

@media (max-width: 480px) {
  .elegant-gallery {
    max-width: 200px;
  }
  
  .gallery-viewport {
    height: 130px;
  }
}
</style>

<script>
class ElegantGallery {
  constructor() {
    this.currentIndex = 0;
    this.slides = document.querySelectorAll('.slide');
    this.totalSlides = this.slides.length;
    this.container = document.querySelector('.slides-container');
    this.isAnimating = false;
    
    this.initEventListeners();
  }
  
  initEventListeners() {
    // Touch events
    let startX = 0;
    let startY = 0;
    let currentX = 0;
    let isDragging = false;
    
    const viewport = document.querySelector('.gallery-viewport');
    
    viewport.addEventListener('touchstart', (e) => {
      startX = e.touches[0].clientX;
      startY = e.touches[0].clientY;
      isDragging = true;
    }, { passive: true });
    
    viewport.addEventListener('touchmove', (e) => {
      if (!isDragging) return;
      currentX = e.touches[0].clientX;
      
      // Prevent vertical scroll if horizontal swipe is detected
      const deltaX = Math.abs(currentX - startX);
      const deltaY = Math.abs(e.touches[0].clientY - startY);
      
      if (deltaX > deltaY && deltaX > 10) {
        e.preventDefault();
      }
    }, { passive: false });
    
    viewport.addEventListener('touchend', () => {
      if (!isDragging) return;
      
      const diff = startX - currentX;
      const threshold = 40;
      
      if (Math.abs(diff) > threshold) {
        if (diff > 0) {
          this.next();
        } else {
          this.previous();
        }
      }
      
      isDragging = false;
    });
    
    // Keyboard navigation
    document.addEventListener('keydown', (e) => {
      if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') return;
      
      if (e.key === 'ArrowLeft') {
        e.preventDefault();
        this.previous();
      } else if (e.key === 'ArrowRight') {
        e.preventDefault();
        this.next();
      }
    });
  }
  
  updateSlides() {
    if (this.isAnimating) return;
    this.isAnimating = true;
    
    const offset = -this.currentIndex * 50;
    this.container.style.transform = `translateX(${offset}%)`;
    
    this.slides.forEach((slide, index) => {
      slide.classList.toggle('active', index === this.currentIndex);
    });
    
    setTimeout(() => {
      this.isAnimating = false;
    }, 600);
  }
  
  next() {
    this.currentIndex = (this.currentIndex + 1) % this.totalSlides;
    this.updateSlides();
  }
  
  previous() {
    this.currentIndex = (this.currentIndex - 1 + this.totalSlides) % this.totalSlides;
    this.updateSlides();
  }
}

// Initialize gallery when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
  if (document.querySelector('.elegant-gallery')) {
    new ElegantGallery();
  }
});

// Fallback functions for inline onclick handlers
function navigateSlide(direction) {
  if (window.galleryInstance) {
    if (direction > 0) {
      window.galleryInstance.next();
    } else {
      window.galleryInstance.previous();
    }
  }
}

// Create global instance
setTimeout(() => {
  if (document.querySelector('.elegant-gallery')) {
    window.galleryInstance = new ElegantGallery();
  }
}, 100);
</script>

