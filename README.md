// Initialize Animations
AOS.init({
    duration: 1000,
    once: true,
    easing: 'ease-out-cubic'
});

// Sticky Navigation & Scroll Progress
window.addEventListener('scroll', () => {
    const nav = document.querySelector('.navbar');
    const progressBar = document.getElementById('progress-bar');
    
    // Sticky Nav logic
    if (window.scrollY > 50) {
        nav.classList.add('sticky');
    } else {
        nav.classList.remove('sticky');
    }

    // Progress Bar logic
    const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
    const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    const scrolled = (winScroll / height) * 100;
    progressBar.style.width = scrolled + "%";
});

// Smooth scroll for nav links (Standard behavior enhanced)
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
    });
});

// Mobile Menu Placeholder (For actual functional menu)
const mobileBtn = document.querySelector('.mobile-menu-btn');
mobileBtn.addEventListener('click', () => {
    alert("Mobile menu functionality can be added here with a slide-out overlay.");
});

// Form Submission Feedback
const contactForm = document.querySelector('.contact-form');
if(contactForm) {
    contactForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const btn = contactForm.querySelector('button');
        btn.innerText = "Message Sent!";
        btn.style.backgroundColor = "#8EA694";
        contactForm.reset();
        setTimeout(() => {
            btn.innerText = "Send Message";
        }, 3000);
    });
}
