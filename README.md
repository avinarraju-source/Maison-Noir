<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Maison Noir — Fine Dining</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Josefin+Sans:wght@100;200;300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0a0805;
    --parchment: #f5efe6;
    --cream: #ede4d4;
    --ember: #c8601a;
    --ember-dim: #8a3f0e;
    --gold: #c9a84c;
    --gold-pale: #e8d49a;
    --moss: #3a4a35;
    --smoke: #6b6560;
    --bone: #d4c9b8;
  }

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
background: var(–ink);
color: var(–parchment);
font-family: ‘Josefin Sans’, sans-serif;
font-weight: 200;
overflow-x: hidden;
cursor: none;
}

/* ── Custom Cursor ── */
.cursor {
position: fixed;
width: 10px; height: 10px;
border-radius: 50%;
background: var(–ember);
pointer-events: none;
z-index: 9999;
transform: translate(-50%, -50%);
transition: transform 0.08s ease, width 0.2s ease, height 0.2s ease, background 0.2s ease;
mix-blend-mode: screen;
}
.cursor-ring {
position: fixed;
width: 36px; height: 36px;
border-radius: 50%;
border: 1px solid var(–gold);
pointer-events: none;
z-index: 9998;
transform: translate(-50%, -50%);
transition: transform 0.18s ease, width 0.25s ease, height 0.25s ease, opacity 0.2s ease;
opacity: 0.6;
}
body:hover .cursor { opacity: 1; }

/* ── Grain Overlay ── */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 256 256’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘noise’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23noise)’ opacity=‘1’/%3E%3C/svg%3E”);
opacity: 0.035;
pointer-events: none;
z-index: 9997;
}

/* ── Nav ── */
nav {
position: fixed;
top: 0; left: 0; right: 0;
z-index: 100;
display: flex;
justify-content: space-between;
align-items: center;
padding: 28px 60px;
background: linear-gradient(to bottom, rgba(10,8,5,0.95) 0%, transparent 100%);
}
.nav-logo {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.1rem;
font-weight: 300;
letter-spacing: 0.35em;
color: var(–gold);
text-transform: uppercase;
}
.nav-links {
display: flex;
gap: 44px;
list-style: none;
}
.nav-links a {
font-size: 0.68rem;
letter-spacing: 0.22em;
text-transform: uppercase;
color: var(–bone);
text-decoration: none;
transition: color 0.3s;
position: relative;
}
.nav-links a::after {
content: ‘’;
position: absolute;
bottom: -4px; left: 0; right: 100%;
height: 1px;
background: var(–ember);
transition: right 0.35s ease;
}
.nav-links a:hover { color: var(–parchment); }
.nav-links a:hover::after { right: 0; }
.nav-reserve {
font-size: 0.62rem;
letter-spacing: 0.22em;
text-transform: uppercase;
border: 1px solid var(–ember);
color: var(–ember);
padding: 10px 22px;
text-decoration: none;
transition: background 0.3s, color 0.3s;
}
.nav-reserve:hover {
background: var(–ember);
color: var(–ink);
}

/* ── Hero ── */
.hero {
position: relative;
height: 100vh;
display: flex;
align-items: center;
justify-content: center;
overflow: hidden;
}
.hero-bg {
position: absolute;
inset: 0;
background:
radial-gradient(ellipse 60% 80% at 20% 50%, rgba(200,96,26,0.08) 0%, transparent 70%),
radial-gradient(ellipse 50% 60% at 80% 30%, rgba(201,168,76,0.05) 0%, transparent 60%),
radial-gradient(ellipse 80% 80% at 50% 100%, rgba(58,74,53,0.15) 0%, transparent 70%);
}
.hero-line-art {
position: absolute;
inset: 0;
overflow: hidden;
}
.hero-line-art svg {
width: 100%; height: 100%;
opacity: 0.07;
}
.hero-content {
text-align: center;
position: relative;
z-index: 2;
animation: heroFade 1.6s ease both;
}
@keyframes heroFade {
from { opacity: 0; transform: translateY(30px); }
to { opacity: 1; transform: translateY(0); }
}
.hero-eyebrow {
font-size: 0.62rem;
letter-spacing: 0.45em;
text-transform: uppercase;
color: var(–ember);
margin-bottom: 28px;
animation: heroFade 1.4s 0.2s ease both;
}
.hero-title {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(5rem, 14vw, 12rem);
font-weight: 300;
line-height: 0.88;
letter-spacing: -0.01em;
color: var(–parchment);
animation: heroFade 1.4s 0.4s ease both;
}
.hero-title em {
font-style: italic;
color: var(–gold);
}
.hero-sub {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.05rem;
font-weight: 300;
font-style: italic;
color: var(–smoke);
margin-top: 28px;
letter-spacing: 0.06em;
animation: heroFade 1.4s 0.6s ease both;
}
.hero-divider {
display: flex;
align-items: center;
justify-content: center;
gap: 16px;
margin-top: 50px;
animation: heroFade 1.4s 0.8s ease both;
}
.hero-divider-line {
width: 80px;
height: 1px;
background: linear-gradient(to right, transparent, var(–gold));
}
.hero-divider-line:last-child {
background: linear-gradient(to left, transparent, var(–gold));
}
.hero-divider-dot {
width: 5px; height: 5px;
border-radius: 50%;
background: var(–ember);
}
.hero-cta {
display: inline-block;
margin-top: 50px;
font-size: 0.62rem;
letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–parchment);
text-decoration: none;
animation: heroFade 1.4s 1s ease both;
transition: color 0.3s;
}
.hero-cta:hover { color: var(–ember); }
.hero-scroll {
position: absolute;
bottom: 40px;
left: 50%;
transform: translateX(-50%);
display: flex;
flex-direction: column;
align-items: center;
gap: 10px;
animation: heroFade 1.4s 1.2s ease both;
}
.hero-scroll span {
font-size: 0.55rem;
letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–smoke);
}
.scroll-line {
width: 1px;
height: 50px;
background: linear-gradient(to bottom, var(–gold), transparent);
animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
0%, 100% { opacity: 0.4; transform: scaleY(0.8); }
50% { opacity: 1; transform: scaleY(1); }
}

/* ── Section Base ── */
section { padding: 120px 60px; }

.section-label {
font-size: 0.58rem;
letter-spacing: 0.45em;
text-transform: uppercase;
color: var(–ember);
margin-bottom: 16px;
}

/* ── About ── */
.about {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 80px;
align-items: center;
max-width: 1200px;
margin: 0 auto;
}
.about-left { position: relative; }
.about-image-frame {
width: 100%;
aspect-ratio: 3/4;
border: 1px solid rgba(201,168,76,0.2);
position: relative;
overflow: hidden;
background:
radial-gradient(ellipse at 30% 40%, rgba(200,96,26,0.15) 0%, transparent 60%),
radial-gradient(ellipse at 70% 80%, rgba(58,74,53,0.2) 0%, transparent 60%),
#141210;
display: flex;
align-items: center;
justify-content: center;
}
.about-image-frame::before {
content: ‘’;
position: absolute;
inset: 12px;
border: 1px solid rgba(201,168,76,0.1);
pointer-events: none;
}
.about-plate-icon {
font-size: 5rem;
opacity: 0.15;
filter: grayscale(1);
}
.about-tag {
position: absolute;
bottom: -20px;
right: -20px;
width: 130px;
height: 130px;
border: 1px solid var(–ember);
display: flex;
align-items: center;
justify-content: center;
background: var(–ink);
font-family: ‘Cormorant Garamond’, serif;
font-size: 0.75rem;
font-weight: 300;
letter-spacing: 0.1em;
text-align: center;
color: var(–gold);
line-height: 1.6;
transform: rotate(5deg);
}
.about-right h2 {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(2.8rem, 5vw, 4.5rem);
font-weight: 300;
line-height: 1.1;
color: var(–parchment);
margin-bottom: 30px;
}
.about-right h2 em {
font-style: italic;
color: var(–gold);
}
.about-right p {
font-size: 0.82rem;
line-height: 2;
color: var(–smoke);
margin-bottom: 20px;
letter-spacing: 0.05em;
}
.about-stats {
display: flex;
gap: 40px;
margin-top: 48px;
padding-top: 40px;
border-top: 1px solid rgba(201,168,76,0.15);
}
.stat-num {
font-family: ‘Cormorant Garamond’, serif;
font-size: 2.8rem;
font-weight: 300;
color: var(–ember);
line-height: 1;
}
.stat-label {
font-size: 0.6rem;
letter-spacing: 0.25em;
text-transform: uppercase;
color: var(–smoke);
margin-top: 6px;
}

/* ── Menu ── */
.menu-section {
background: #0d0b08;
position: relative;
overflow: hidden;
}
.menu-section::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 1px;
background: linear-gradient(to right, transparent, var(–gold), transparent);
opacity: 0.3;
}
.menu-section::after {
content: ‘’;
position: absolute;
bottom: 0; left: 0; right: 0;
height: 1px;
background: linear-gradient(to right, transparent, var(–gold), transparent);
opacity: 0.3;
}
.menu-inner { max-width: 1200px; margin: 0 auto; }
.menu-header {
display: flex;
justify-content: space-between;
align-items: flex-end;
margin-bottom: 70px;
}
.menu-header h2 {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(3rem, 6vw, 5rem);
font-weight: 300;
color: var(–parchment);
line-height: 1;
}
.menu-header h2 em { color: var(–gold); font-style: italic; }
.menu-season {
font-size: 0.62rem;
letter-spacing: 0.3em;
text-transform: uppercase;
color: var(–smoke);
border-left: 2px solid var(–ember);
padding-left: 16px;
}
.menu-tabs {
display: flex;
gap: 0;
margin-bottom: 60px;
border-bottom: 1px solid rgba(201,168,76,0.15);
}
.menu-tab {
font-size: 0.62rem;
letter-spacing: 0.3em;
text-transform: uppercase;
color: var(–smoke);
padding: 12px 28px 14px;
cursor: pointer;
border: none;
background: none;
position: relative;
transition: color 0.3s;
font-family: ‘Josefin Sans’, sans-serif;
font-weight: 200;
}
.menu-tab.active { color: var(–parchment); }
.menu-tab.active::after {
content: ‘’;
position: absolute;
bottom: -1px; left: 0; right: 0;
height: 1px;
background: var(–ember);
}
.menu-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 2px;
}
.menu-item {
padding: 32px 0;
border-bottom: 1px solid rgba(201,168,76,0.08);
display: flex;
justify-content: space-between;
align-items: flex-start;
gap: 24px;
cursor: pointer;
transition: background 0.2s;
padding-left: 20px;
padding-right: 20px;
margin: 0 -20px;
}
.menu-item:hover { background: rgba(200,96,26,0.04); }
.menu-item:hover .item-name { color: var(–gold); }
.item-info { flex: 1; }
.item-name {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.25rem;
font-weight: 400;
color: var(–parchment);
margin-bottom: 6px;
transition: color 0.3s;
}
.item-desc {
font-size: 0.68rem;
letter-spacing: 0.06em;
color: var(–smoke);
line-height: 1.7;
}
.item-price {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.1rem;
font-weight: 300;
color: var(–ember);
white-space: nowrap;
margin-top: 2px;
}

/* ── Experience Band ── */
.experience-band {
position: relative;
padding: 100px 60px;
background:
radial-gradient(ellipse 70% 100% at 50% 50%, rgba(200,96,26,0.06) 0%, transparent 70%),
var(–ink);
text-align: center;
overflow: hidden;
}
.exp-bg-text {
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(8rem, 22vw, 20rem);
font-weight: 300;
font-style: italic;
color: rgba(201,168,76,0.04);
white-space: nowrap;
pointer-events: none;
user-select: none;
}
.exp-content { position: relative; z-index: 2; max-width: 700px; margin: 0 auto; }
.exp-content h2 {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(2.5rem, 5vw, 4rem);
font-weight: 300;
color: var(–parchment);
line-height: 1.2;
margin-bottom: 28px;
}
.exp-content h2 em { color: var(–gold); font-style: italic; }
.exp-content p {
font-size: 0.78rem;
color: var(–smoke);
line-height: 2.1;
letter-spacing: 0.08em;
margin-bottom: 50px;
}
.exp-grid {
display: flex;
justify-content: center;
gap: 60px;
margin-top: 60px;
}
.exp-item {
display: flex;
flex-direction: column;
align-items: center;
gap: 14px;
}
.exp-icon {
width: 52px; height: 52px;
border: 1px solid rgba(201,168,76,0.25);
border-radius: 50%;
display: flex;
align-items: center;
justify-content: center;
font-size: 1.2rem;
}
.exp-label {
font-size: 0.6rem;
letter-spacing: 0.3em;
text-transform: uppercase;
color: var(–smoke);
}

/* ── Reservations ── */
.reservations {
max-width: 1000px;
margin: 0 auto;
display: grid;
grid-template-columns: 1fr 1fr;
gap: 80px;
align-items: center;
}
.res-left h2 {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(2.5rem, 4vw, 3.8rem);
font-weight: 300;
color: var(–parchment);
line-height: 1.1;
margin-bottom: 24px;
}
.res-left h2 em { color: var(–gold); font-style: italic; }
.res-left p {
font-size: 0.75rem;
color: var(–smoke);
line-height: 2;
margin-bottom: 14px;
}
.res-info-row {
display: flex;
flex-direction: column;
gap: 16px;
margin-top: 36px;
padding-top: 36px;
border-top: 1px solid rgba(201,168,76,0.12);
}
.res-info-item {
display: flex;
gap: 16px;
align-items: flex-start;
}
.res-info-key {
font-size: 0.58rem;
letter-spacing: 0.3em;
text-transform: uppercase;
color: var(–ember);
min-width: 90px;
padding-top: 2px;
}
.res-info-val {
font-size: 0.75rem;
color: var(–parchment);
line-height: 1.7;
letter-spacing: 0.05em;
}
.res-right {
background: #0d0b08;
border: 1px solid rgba(201,168,76,0.12);
padding: 50px 40px;
position: relative;
}
.res-right::before {
content: ‘’;
position: absolute;
top: 10px; left: 10px; right: 10px; bottom: 10px;
border: 1px solid rgba(201,168,76,0.05);
pointer-events: none;
}
.form-group {
margin-bottom: 28px;
}
.form-label {
display: block;
font-size: 0.58rem;
letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–smoke);
margin-bottom: 10px;
}
.form-input {
width: 100%;
background: transparent;
border: none;
border-bottom: 1px solid rgba(201,168,76,0.2);
padding: 10px 0;
font-family: ‘Josefin Sans’, sans-serif;
font-size: 0.78rem;
font-weight: 200;
color: var(–parchment);
letter-spacing: 0.08em;
outline: none;
transition: border-color 0.3s;
}
.form-input:focus { border-color: var(–ember); }
.form-input::placeholder { color: rgba(107,101,96,0.5); }
.form-select {
width: 100%;
background: transparent;
border: none;
border-bottom: 1px solid rgba(201,168,76,0.2);
padding: 10px 0;
font-family: ‘Josefin Sans’, sans-serif;
font-size: 0.78rem;
font-weight: 200;
color: var(–parchment);
letter-spacing: 0.08em;
outline: none;
appearance: none;
cursor: pointer;
}
.form-select option { background: #0d0b08; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
.btn-reserve {
width: 100%;
background: var(–ember);
border: none;
padding: 18px;
font-family: ‘Josefin Sans’, sans-serif;
font-size: 0.65rem;
font-weight: 300;
letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–ink);
cursor: pointer;
margin-top: 10px;
transition: background 0.3s, color 0.3s;
position: relative;
overflow: hidden;
}
.btn-reserve::before {
content: ‘’;
position: absolute;
inset: 0;
background: var(–gold);
transform: scaleX(0);
transform-origin: left;
transition: transform 0.4s ease;
}
.btn-reserve:hover::before { transform: scaleX(1); }
.btn-reserve span { position: relative; z-index: 1; }

/* ── Footer ── */
footer {
padding: 60px;
border-top: 1px solid rgba(201,168,76,0.1);
display: flex;
justify-content: space-between;
align-items: center;
}
.footer-logo {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.6rem;
font-weight: 300;
letter-spacing: 0.2em;
color: var(–gold);
}
.footer-copy {
font-size: 0.58rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–smoke);
}
.footer-social {
display: flex;
gap: 24px;
}
.footer-social a {
font-size: 0.6rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–smoke);
text-decoration: none;
transition: color 0.3s;
}
.footer-social a:hover { color: var(–ember); }

/* ── Parallax strips ── */
.parallax-strip {
height: 1px;
background: linear-gradient(to right, transparent, rgba(201,168,76,0.2), transparent);
margin: 0;
}

/* ── Scroll reveal ── */
.reveal {
opacity: 0;
transform: translateY(40px);
transition: opacity 0.9s ease, transform 0.9s ease;
}
.reveal.visible {
opacity: 1;
transform: translateY(0);
}
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.35s; }
.reveal-delay-4 { transition-delay: 0.5s; }

/* ── Hero image bg ── */
.hero-img {
position: absolute;
inset: 0;
background-image: url(‘https://images.unsplash.com/photo-1414235077428-338989a2e8c0?w=1800&q=80’);
background-size: cover;
background-position: center;
opacity: 0.18;
filter: grayscale(40%) contrast(1.1);
}

/* ── About image ── */
.about-image-frame {
background-image: url(‘https://images.unsplash.com/photo-1600565193348-f74bd3c7ccdf?w=900&q=80’) !important;
background-size: cover !important;
background-position: center !important;
}
.about-image-frame .about-plate-icon { display: none; }

/* ── Photo Strip / Gallery ── */
.photo-strip {
display: grid;
grid-template-columns: 2fr 1fr 1fr;
grid-template-rows: 400px;
gap: 3px;
overflow: hidden;
}
.photo-strip-item {
overflow: hidden;
position: relative;
}
.photo-strip-item img {
width: 100%;
height: 100%;
object-fit: cover;
filter: grayscale(20%) contrast(1.05) brightness(0.85);
transition: transform 0.7s ease, filter 0.5s ease;
}
.photo-strip-item:hover img {
transform: scale(1.06);
filter: grayscale(0%) contrast(1.05) brightness(0.9);
}
.photo-strip-item::after {
content: ‘’;
position: absolute;
inset: 0;
background: linear-gradient(to top, rgba(10,8,5,0.5) 0%, transparent 50%);
pointer-events: none;
}
.photo-strip-right {
display: grid;
grid-template-rows: 1fr 1fr;
gap: 3px;
}

/* ── Atmosphere full-width ── */
.atmosphere {
position: relative;
height: 70vh;
overflow: hidden;
display: flex;
align-items: center;
justify-content: center;
}
.atmosphere img {
position: absolute;
inset: 0;
width: 100%;
height: 100%;
object-fit: cover;
filter: grayscale(30%) brightness(0.45) contrast(1.1);
}
.atmosphere-overlay {
position: relative;
z-index: 2;
text-align: center;
padding: 40px;
}
.atmosphere-overlay blockquote {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(1.8rem, 4vw, 3.2rem);
font-weight: 300;
font-style: italic;
color: var(–parchment);
max-width: 800px;
line-height: 1.4;
letter-spacing: 0.02em;
}
.atmosphere-overlay cite {
display: block;
font-family: ‘Josefin Sans’, sans-serif;
font-size: 0.6rem;
font-weight: 200;
letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–ember);
margin-top: 24px;
font-style: normal;
}

/* ── Menu item thumbnails ── */
.menu-item-img {
width: 70px;
height: 70px;
object-fit: cover;
flex-shrink: 0;
filter: grayscale(20%) brightness(0.85);
border: 1px solid rgba(201,168,76,0.12);
transition: filter 0.4s ease;
}
.menu-item:hover .menu-item-img {
filter: grayscale(0%) brightness(1);
}

/* ── Chef section ── */
.chef-section {
padding: 120px 60px;
max-width: 1200px;
margin: 0 auto;
display: grid;
grid-template-columns: 1fr 1fr;
gap: 80px;
align-items: center;
}
.chef-img-wrap {
position: relative;
}
.chef-img-wrap img {
width: 100%;
aspect-ratio: 4/5;
object-fit: cover;
object-position: center top;
filter: grayscale(15%) contrast(1.05) brightness(0.88);
border: 1px solid rgba(201,168,76,0.15);
}
.chef-img-wrap::after {
content: ‘’;
position: absolute;
bottom: -16px;
right: -16px;
width: 60%;
height: 60%;
border: 1px solid rgba(200,96,26,0.25);
pointer-events: none;
z-index: -1;
}
.chef-text .section-label { margin-bottom: 16px; }
.chef-text h2 {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(2.5rem, 4vw, 3.8rem);
font-weight: 300;
color: var(–parchment);
line-height: 1.1;
margin-bottom: 24px;
}
.chef-text h2 em { color: var(–gold); font-style: italic; }
.chef-text p {
font-size: 0.8rem;
color: var(–smoke);
line-height: 2;
letter-spacing: 0.05em;
margin-bottom: 16px;
}
.chef-sig {
font-family: ‘Cormorant Garamond’, serif;
font-size: 1.8rem;
font-weight: 300;
font-style: italic;
color: var(–gold);
margin-top: 30px;
}

/* ── Responsive ── */
@media (max-width: 900px) {
nav { padding: 20px 24px; }
.nav-links { display: none; }
section { padding: 80px 24px; }
.about { grid-template-columns: 1fr; gap: 60px; }
.about-tag { display: none; }
.menu-grid { grid-template-columns: 1fr; }
.menu-header { flex-direction: column; align-items: flex-start; gap: 20px; }
.reservations { grid-template-columns: 1fr; gap: 60px; }
footer { flex-direction: column; gap: 28px; text-align: center; }
.exp-grid { flex-wrap: wrap; gap: 40px; }
.photo-strip { grid-template-columns: 1fr; grid-template-rows: auto; }
.photo-strip-right { grid-template-rows: 220px 220px; }
.photo-strip-item { height: 280px; }
.chef-section { grid-template-columns: 1fr; gap: 50px; padding: 80px 24px; }
.atmosphere { height: 50vh; }
}
</style>

</head>
<body>

<!-- Custom cursor -->

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Nav -->

<nav>
  <div class="nav-logo">Maison Noir</div>
  <ul class="nav-links">
    <li><a href="#about">Our Story</a></li>
    <li><a href="#menu">Menu</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#reserve">Reserve</a></li>
  </ul>
  <a href="#reserve" class="nav-reserve">Reserve a Table</a>
</nav>

<!-- Hero -->

<section class="hero">
  <div class="hero-img"></div>
  <div class="hero-bg"></div>
  <div class="hero-line-art">
    <svg viewBox="0 0 1200 800" preserveAspectRatio="xMidYMid slice" fill="none" stroke="currentColor" stroke-width="0.5">
      <circle cx="600" cy="400" r="280"/>
      <circle cx="600" cy="400" r="220"/>
      <circle cx="600" cy="400" r="340"/>
      <line x1="0" y1="400" x2="1200" y2="400"/>
      <line x1="600" y1="0" x2="600" y2="800"/>
      <line x1="0" y1="0" x2="1200" y2="800"/>
      <line x1="1200" y1="0" x2="0" y2="800"/>
      <polygon points="600,120 880,400 600,680 320,400"/>
      <polygon points="600,200 800,400 600,600 400,400"/>
    </svg>
  </div>
  <div class="hero-content">
    <p class="hero-eyebrow">Est. 2019 · San Francisco</p>
    <h1 class="hero-title">Maison<br><em>Noir</em></h1>
    <p class="hero-sub">Where darkness holds its own kind of warmth</p>
    <div class="hero-divider">
      <div class="hero-divider-line"></div>
      <div class="hero-divider-dot"></div>
      <div class="hero-divider-line"></div>
    </div>
    <a href="#menu" class="hero-cta">Explore the Menu ↓</a>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<div class="parallax-strip"></div>

<!-- About -->

<section id="about">
  <div class="about">
    <div class="about-left reveal">
      <div class="about-image-frame">
        <div class="about-plate-icon">🍽</div>
      </div>
      <div class="about-tag">Since<br>2019<br>––<br>SF</div>
    </div>
    <div class="about-right">
      <p class="section-label reveal reveal-delay-1">Our Philosophy</p>
      <h2 class="reveal reveal-delay-2">Food as <em>ritual</em>,<br>dining as ceremony</h2>
      <p class="reveal reveal-delay-3">Maison Noir was born from the belief that a great meal is not merely consumed — it is experienced. We source from a constellation of small California farms and coastal purveyors, letting the season write the menu.</p>
      <p class="reveal reveal-delay-3">Each dish is composed with restraint, allowing a single ingredient to speak with clarity, elevated by technique honed across decades in Lyon, Tokyo, and Copenhagen.</p>
      <div class="about-stats reveal reveal-delay-4">
        <div>
          <div class="stat-num">12</div>
          <div class="stat-label">Seats per service</div>
        </div>
        <div>
          <div class="stat-num">3</div>
          <div class="stat-label">Michelin stars</div>
        </div>
        <div>
          <div class="stat-num">7</div>
          <div class="stat-label">Course tasting menu</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Photo Strip -->

<div class="photo-strip">
  <div class="photo-strip-item">
    <img src="https://images.unsplash.com/photo-1559339352-11d035aa65de?w=1200&q=80" alt="Restaurant interior">
  </div>
  <div class="photo-strip-right">
    <div class="photo-strip-item">
      <img src="https://images.unsplash.com/photo-1578474846511-04ba529f0b88?w=800&q=80" alt="Plated dish">
    </div>
    <div class="photo-strip-item">
      <img src="https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=800&q=80" alt="Gourmet food">
    </div>
  </div>
  <div class="photo-strip-right">
    <div class="photo-strip-item">
      <img src="https://images.unsplash.com/photo-1567620905732-2d1ec7ab7445?w=800&q=80" alt="Food detail">
    </div>
    <div class="photo-strip-item">
      <img src="https://images.unsplash.com/photo-1414235077428-338989a2e8c0?w=800&q=80" alt="Dining room">
    </div>
  </div>
</div>

<div class="parallax-strip"></div>

<!-- Menu -->

<section class="menu-section" id="menu">
  <div class="menu-inner">
    <div class="menu-header reveal">
      <div>
        <p class="section-label">Tasting Menu</p>
        <h2>Tonight's<br><em>Selection</em></h2>
      </div>
      <p class="menu-season">Spring / Summer 2026</p>
    </div>
    <div class="menu-tabs reveal reveal-delay-1">
      <button class="menu-tab active" onclick="switchTab(this, 'amuse')">Amuse</button>
      <button class="menu-tab" onclick="switchTab(this, 'first')">First</button>
      <button class="menu-tab" onclick="switchTab(this, 'main')">Main</button>
      <button class="menu-tab" onclick="switchTab(this, 'dessert')">Dessert</button>
    </div>
    <div class="menu-grid" id="menu-grid">
      <!-- Amuse courses -->
      <div class="menu-item reveal">
        <img src="https://images.unsplash.com/photo-1519984388953-d2406bc725e1?w=200&q=80" alt="Caviar" class="menu-item-img">
        <div class="item-info">
          <div class="item-name">Caviar & Crème Fraîche</div>
          <div class="item-desc">Ossetra on buckwheat blini · preserved lemon · chive oil</div>
        </div>
        <div class="item-price">–</div>
      </div>
      <div class="menu-item reveal reveal-delay-1">
        <img src="https://images.unsplash.com/photo-1547592180-85f173990554?w=200&q=80" alt="Dashi custard" class="menu-item-img">
        <div class="item-info">
          <div class="item-name">Dashi Custard</div>
          <div class="item-desc">Kombu · miso butter · bottarga · micro shiso</div>
        </div>
        <div class="item-price">–</div>
      </div>
      <div class="menu-item reveal reveal-delay-2">
        <img src="https://images.unsplash.com/photo-1615141982883-c7ad0e69fd62?w=200&q=80" alt="Oyster" class="menu-item-img">
        <div class="item-info">
          <div class="item-name">Smoked Oyster</div>
          <div class="item-desc">Cold-smoked · cucumber granita · champagne mignonette</div>
        </div>
        <div class="item-price">–</div>
      </div>
      <div class="menu-item reveal reveal-delay-3">
        <img src="https://images.unsplash.com/photo-1551024709-8f23befc6f87?w=200&q=80" alt="Foie gras" class="menu-item-img">
        <div class="item-info">
          <div class="item-name">Foie Gras Torchon</div>
          <div class="item-desc">Fig mostarda · brioche · aged balsamic</div>
        </div>
        <div class="item-price">–</div>
      </div>
    </div>
    <div style="margin-top: 48px; display: flex; justify-content: center;">
      <p style="font-size:0.65rem; letter-spacing:0.3em; text-transform:uppercase; color:var(--smoke);">
        Full tasting menu · $285 per person · wine pairing +$145
      </p>
    </div>
  </div>
</section>

<div class="parallax-strip"></div>

<!-- Atmosphere Full-Width -->

<div class="atmosphere">
  <img src="https://images.unsplash.com/photo-1424847651672-bf20a4b0982b?w=1800&q=80" alt="Restaurant ambiance">
  <div class="atmosphere-overlay reveal">
    <blockquote>"The table is the only place where one is never bored for the first hour."</blockquote>
    <cite>Jean-Anthelme Brillat-Savarin</cite>
  </div>
</div>

<!-- Experience Band -->

<section class="experience-band" id="experience">
  <div class="exp-bg-text">Noir</div>
  <div class="exp-content">
    <p class="section-label reveal">The Experience</p>
    <h2 class="reveal reveal-delay-1">An evening<br>you won't <em>forget</em></h2>
    <p class="reveal reveal-delay-2">From the moment you descend into our subterranean dining room, sound softens, light warms, and time slows. Every detail — the weight of the silverware, the temperature of the room, the arc of the evening — is considered.</p>
    <div class="exp-grid reveal reveal-delay-3">
      <div class="exp-item">
        <div class="exp-icon">🕯</div>
        <div class="exp-label">Candlelit only</div>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🍷</div>
        <div class="exp-label">Natural wines</div>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🌿</div>
        <div class="exp-label">Farm to table</div>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🎻</div>
        <div class="exp-label">Live quartet</div>
      </div>
    </div>
  </div>
</section>

<div class="parallax-strip"></div>

<!-- Chef Section -->

<div class="chef-section">
  <div class="chef-img-wrap reveal">
    <img src="https://images.unsplash.com/photo-1577219491135-ce391730fb2c?w=900&q=80" alt="Executive Chef">
  </div>
  <div class="chef-text">
    <p class="section-label reveal reveal-delay-1">The Kitchen</p>
    <h2 class="reveal reveal-delay-2">Chef <em>Laurent</em><br>Beausoleil</h2>
    <p class="reveal reveal-delay-3">Trained under Alain Ducasse in Paris and later at Noma in Copenhagen, Laurent spent a decade studying the quiet discipline of Japanese kaiseki before returning to California to open Maison Noir.</p>
    <p class="reveal reveal-delay-3">His philosophy is deceptively simple: find the finest ingredient, then have the confidence to leave it nearly alone. The result is cooking of rare clarity — precise without being cold, inventive without being clever.</p>
    <div class="chef-sig reveal reveal-delay-4">Laurent B.</div>
  </div>
</div>

<div class="parallax-strip"></div>
<section id="reserve">
  <div class="reservations">
    <div class="res-left">
      <p class="section-label reveal">Reserve</p>
      <h2 class="reveal reveal-delay-1">Secure your<br><em>evening</em></h2>
      <p class="reveal reveal-delay-2">We offer two seatings nightly: 6:00 pm and 9:00 pm, Wednesday through Sunday. Reservations are required and held for 10 minutes past the reservation time.</p>
      <div class="res-info-row reveal reveal-delay-3">
        <div class="res-info-item">
          <span class="res-info-key">Hours</span>
          <span class="res-info-val">Wed–Sun · 5:30 pm – midnight</span>
        </div>
        <div class="res-info-item">
          <span class="res-info-key">Location</span>
          <span class="res-info-val">42 Waverly Place, San Francisco CA 94108</span>
        </div>
        <div class="res-info-item">
          <span class="res-info-key">Phone</span>
          <span class="res-info-val">+1 (415) 000–0000</span>
        </div>
        <div class="res-info-item">
          <span class="res-info-key">Dress</span>
          <span class="res-info-val">Smart casual to formal encouraged</span>
        </div>
      </div>
    </div>
    <div class="res-right reveal reveal-delay-2">
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">First Name</label>
          <input type="text" class="form-input" placeholder="Henri">
        </div>
        <div class="form-group">
          <label class="form-label">Last Name</label>
          <input type="text" class="form-input" placeholder="Beaumont">
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Email</label>
        <input type="email" class="form-input" placeholder="hello@example.com">
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Date</label>
          <input type="date" class="form-input">
        </div>
        <div class="form-group">
          <label class="form-label">Seating</label>
          <select class="form-select">
            <option>6:00 pm</option>
            <option>9:00 pm</option>
          </select>
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Party Size</label>
        <select class="form-select">
          <option>1 guest</option>
          <option>2 guests</option>
          <option>3 guests</option>
          <option>4 guests</option>
          <option>Private dining (5+)</option>
        </select>
      </div>
      <button class="btn-reserve"><span>Request Reservation</span></button>
    </div>
  </div>
</section>

<!-- Footer -->

<footer>
  <div class="footer-logo">MN</div>
  <p class="footer-copy">© 2026 Maison Noir · San Francisco</p>
  <div class="footer-social">
    <a href="#">Instagram</a>
    <a href="#">Press</a>
    <a href="#">Careers</a>
  </div>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animateCursor() {
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateCursor);
  }
  animateCursor();
  document.querySelectorAll('a, button, .menu-item').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '18px';
      cursor.style.height = '18px';
      ring.style.width = '54px';
      ring.style.height = '54px';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '10px';
      cursor.style.height = '10px';
      ring.style.width = '36px';
      ring.style.height = '36px';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.12 });
  reveals.forEach(r => io.observe(r));

  // Menu tabs (visual only – just highlights tab)
  function switchTab(btn, section) {
    document.querySelectorAll('.menu-tab').forEach(t => t.classList.remove('active'));
    btn.classList.add('active');
  }

  // Subtle parallax on hero
  window.addEventListener('scroll', () => {
    const y = window.scrollY;
    document.querySelector('.hero-content').style.transform = `translateY(${y * 0.25}px)`;
    document.querySelector('.hero-bg').style.transform = `translateY(${y * 0.15}px)`;
  });
</script>

</body>
</html>
