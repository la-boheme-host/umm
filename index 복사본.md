---
title: "[아이유] 이별로부터 내 영혼의 단짝까지"
layout: splash
author_profile: false
# header:
#  overlay_color: "#000"
#  overlay_filter: "0.3"
#  overlay_image: /assets/images/245/img_1.jpg
#  actions:
#    - label: "Read more"
#      url: "/245"
#excerpt: "아이유의 이번 새 싱글 앨범에는 이별에 관한 노래와 아이유에겐 연상이지만 가장 친한 친구인 유인나를 위한 우정을 노래한 곡 2곡이 담겼습니다. "
---

<!-- 1. 지킬(Liquid) 변수 선언: 최신 포스팅과 이미지 데이터를 먼저 찾아옵니다. -->
{% assign latest_post = site.posts.first %}
{% assign latest_img = latest_post.header.overlay_image | default: latest_post.teaser | default: '/assets/images/default-hero.jpg' %}

<!-- CSS 스타일 정의 -->
<style>
  .custom-hero-wrapper {
    width: 100vw;
    position: relative;
    left: 50%;
    right: 50%;
    margin-left: -50vw;
    margin-right: -50vw;
    margin-bottom: 2rem;
    /* 베이스가 되는 연한 파스텔 투톤 그라데이션 */
    background: linear-gradient(135deg, #e3eeff 0%, #f3e7e9 100%);
    padding: 6rem 0;
    overflow: hidden;
  }
  
  /* 배경 이미지용 가상 레이어 (블러 및 투명도 적용) */
  .custom-hero-wrapper::before {
    content: "";
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background-image: url('{{ latest_img | relative_url }}');
    background-size: cover;
    background-position: center;
    
    /* 투명도와 블러 효과 조절 */
    opacity: 10;
    filter: blur(10px);
    
    /* 블러 처리 시 화면 가장자리가 하얗게 뜨는 현상을 방지하기 위해 크기를 살짝 키움 */
    transform: scale(1.1);
    z-index: 1;
  }
  
  .custom-hero-inner {
    position: relative;
    z-index: 2; /* 텍스트와 CD 이미지가 블러 배경 위로 올라오도록 설정 */
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1em;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 4rem;
  }
  
  /* 왼쪽 텍스트 영역 */
  .custom-hero-text {
    flex: 1;
    text-align: left;
  }
  
  .custom-hero-text h1 {
    font-size: 2rem; 
    margin-bottom: 1rem;
    color: #ffffff; 
    line-height: 1.4;
    font-weight: 800;
  }
  
  .custom-hero-text p {
    font-size: 1.15rem;
    line-height: 1.6;
    margin-bottom: 2rem;
    color: #ffffff; /* 블러 배경에 묻히지 않도록 글씨 색상을 살짝 더 진하게 조정 */
  }
  
  /* 순정 버튼 스타일 */
  .custom-hero-btn {
    display: inline-block;
    padding: 12px 24px;
    background-color: transparent;
    color: #333333;
    border: 2px solid #333333;
    border-radius: 4px;
    text-decoration: none;
    font-weight: bold;
    transition: all 0.3s ease;
  }
  
  .custom-hero-btn:hover {
    background-color: #333333;
    color: #ffffff;
  }
  
  /* 오른쪽 3D CD 케이스 이미지 영역 */
  .custom-hero-visual {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    perspective: 1000px; 
  }
  
  .cd-case-img {
    width: 100%;
    max-width: 400px;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    transform: rotateY(-20deg) rotateX(5deg) scale(1.05);
    box-shadow: 
      -1px 0px 1px #222222,
      -2px 0px 1px #999999,
      -3px 0px 1px #999999,
      -4px 0px 1px #999999,
      -5px 0px 1px #999999,
      -35px 25px 45px rgba(0, 0, 0, 0.15);
    border-radius: 2px 6px 6px 2px;
    transition: transform 0.5s ease, box-shadow 0.5s ease;
  }
  
  .cd-case-img:hover {
    transform: rotateY(-5deg) rotateX(2deg) scale(1.1);
    box-shadow: 
      -1px 0px 1px #222222,
      -2px 0px 1px #999999,
      -3px 0px 1px #999999,
      -40px 35px 55px rgba(0, 0, 0, 0.12);
  }
  
  @media (max-width: 768px) {
    .custom-hero-inner {
      flex-direction: column;
      padding: 0 2em;
    }
    .custom-hero-visual {
      margin-top: 2rem;
    }
  }
</style>

<!-- 2. 풀와이드 동적 히어로 영역 -->
<div class="custom-hero-wrapper">
  <div class="custom-hero-inner">
    
    <div class="custom-hero-text">
      <h1>{{ latest_post.title }}</h1>
      <p>{{ latest_post.excerpt | strip_html | truncate: 100 }}</p>
      <a href="{{ latest_post.url | relative_url }}" class="custom-hero-btn">Read more</a>
    </div>
    
    <div class="custom-hero-visual">
      <img src="{{ latest_img | relative_url }}" alt="{{ latest_post.title }}" class="cd-case-img">
    </div>
    
  </div>
</div>

<style>
  /* 기본 여백 제거 및 중앙 정렬 컨테이너 */
  .page__inner-wrap {
    max-width: 100% !important;
    padding-left: 0 !important;
    padding-right: 0 !important;
  }
  .content-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1em;
  }

  /* =========================================
     랜덤 가사 인트로 영역 CSS (여백 50% 축소)
     ========================================= */
  .custom-intro {
    text-align: center;
    padding: 30px 20px 20px; /* 기존 60px 20px 40px 에서 상하 여백 대폭 감소 */
    margin-bottom: 10px;     /* 기존 20px 에서 10px로 감소 */
  }
  .custom-intro .lyric-text {
    font-style: italic; 
    font-size: 1.2rem;
    color: #333;
    margin-bottom: 15px;
  }
  .custom-intro .lyric-artist {
    font-size: 0.95rem;
    color: #666;
  }

  /* =========================================
     피처 로우 영역 CSS (여백 50% 축소)
     ========================================= */
  .feature-row { 
    display: flex; 
    flex-direction: column; 
    align-items: flex-start; 
    gap: 40px; 
    padding: 30px 0; /* 기존 60px 에서 30px로 상하 간격 감소 */
    border-bottom: 1px solid #f2f3f3; 
  }
  .feature-row:last-of-type { border-bottom: none; }
  
  @media (min-width: 768px) {
    .feature-row { flex-direction: row; }
    .feature-row.reverse { flex-direction: row-reverse; } 
    .feature-row.reverse .feature-text { text-align: right; align-items: flex-end; }
  }
  
  .feature-img { flex: 1; width: 100%; }
  .feature-img img { width: 100%; height: auto; border-radius: 4px; display: block; }
  
  .feature-text { 
    flex: 1; 
    display: flex; 
    flex-direction: column; 
    justify-content: flex-start; 
    align-items: flex-start; 
    padding: 0; 
  }
  .feature-text h2 { margin-top: 0; font-size: 1.5rem; font-weight: bold; margin-bottom: 15px; }
  .feature-text p { color: #494e52; line-height: 1.6; margin-bottom: 25px; }
  
  /* =========================================
     CD 커버 갤러리 영역 CSS 
     ========================================= */
  .custom-gallery-grid { display: grid; gap: 24px; margin-top: 2em; grid-template-columns: repeat(1, 1fr); }
  @media (min-width: 768px) { .custom-gallery-grid { grid-template-columns: repeat(2, 1fr); } }
  @media (min-width: 1024px) { .custom-gallery-grid { grid-template-columns: repeat(4, 1fr); } }
  .custom-gallery-item { position: relative; overflow: hidden; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
  .custom-gallery-item img { width: 100%; aspect-ratio: 1 / 1; object-fit: cover; display: block; transition: transform 0.3s ease; }
  .gallery-overlay { position: absolute; bottom: 0; left: 0; right: 0; background: rgba(0, 0, 0, 0.7); color: #ffffff; padding: 15px; text-align: center; font-weight: bold; font-size: 1rem; transform: translateY(100%); transition: transform 0.3s ease; pointer-events: none; }
  .custom-gallery-item:hover img { transform: scale(1.05); }
  .custom-gallery-item:hover .gallery-overlay { transform: translateY(0); }
  .hidden-item { display: none; }
</style>

<div class="content-container">

  <!-- 랜덤 가사 출력 HTML 영역 -->
  <div class="custom-intro">
    <div class="lyric-text" id="random-lyric-text">"..."</div>
    <div class="lyric-artist" id="random-lyric-artist">- -</div>
  </div>
  
  <!-- 구분선 -->
  <hr style="border: 0; border-top: 1px solid #f2f3f3; margin: 0;">

  <!-- 피처 로우 영역 (시작 마진 50% 축소) -->
  <div style="margin-top: 10px;"> <!-- 기존 20px 에서 10px로 감소 -->
    {% for post in site.posts limit:2 offset:1 %}
      <div class="feature-row {% if forloop.index == 2 %}reverse{% endif %}">
        <div class="feature-img">
          <a href="{{ post.url }}">
            <img src="{{ post.teaser }}" alt="{{ post.title }}">
          </a>
        </div>
        <div class="feature-text">
          <h2>{{ post.title }}</h2>
          <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
          <a href="{{ post.url }}" class="btn btn--danger">Read More</a>
        </div>
      </div>
    {% endfor %}
  </div>

  <!-- 무한 스크롤 갤러리 영역 (상단 마진 50% 축소) -->
  <h2 style="text-align: center; margin-top: 40px; margin-bottom: 20px;">More Music Collection</h2> <!-- 기존 80px 에서 40px로 감소 -->
  
  <div class="custom-gallery-grid" id="gallery-grid">
    {% for post in site.posts offset:3 %}
      {% if post.teaser %}
        <div class="custom-gallery-item gallery-item-card">
          <a href="{{ post.url }}">
            <img src="{{ post.teaser }}" alt="{{ post.title }}">
            <div class="gallery-overlay">{{ post.title }}</div>
          </a>
        </div>
      {% endif %}
    {% endfor %}
  </div>

  <div id="scroll-sentinel" style="height: 20px; margin-top: 40px; margin-bottom: 40px;"></div>

</div>

<!-- 자바스크립트 영역 -->
<script>
  document.addEventListener("DOMContentLoaded", function() {
    
    // 랜덤 가사 자바스크립트 로직 (innerHTML 적용 완료)
    const lyricsList = [
      {% for lyric in site.data.lyrics %}
        { text: "{{ lyric.text }}", artist: "{{ lyric.artist }}" }{% unless forloop.last %},{% endunless %}
      {% endfor %}
    ];

    if (lyricsList.length > 0) {
      const randomIndex = Math.floor(Math.random() * lyricsList.length);
      const selectedLyric = lyricsList[randomIndex];

      document.getElementById('random-lyric-text').innerHTML = '"' + selectedLyric.text + '"';
      document.getElementById('random-lyric-artist').innerHTML = "- " + selectedLyric.artist;
    }

    // 무한 스크롤 자바스크립트 로직
    const items = document.querySelectorAll('.gallery-item-card');
    const sentinel = document.getElementById('scroll-sentinel');
    let currentVisible = 16;
    const loadStep = 16;

    for (let i = 0; i < items.length; i++) {
      if (i >= currentVisible) {
        items[i].classList.add('hidden-item');
      }
    }

    if (items.length <= currentVisible && sentinel) {
      sentinel.style.display = 'none';
    } else if (sentinel) {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            let shown = 0;
            for (let i = 0; i < items.length; i++) {
              if (items[i].classList.contains('hidden-item') && shown < loadStep) { 
                items[i].classList.remove('hidden-item');
                shown++;
                currentVisible++;
              }
            }
            if (currentVisible >= items.length) {
              observer.unobserve(sentinel);
              sentinel.style.display = 'none';
            }
          }
        });
      }, {
        rootMargin: "0px 0px 300px 0px" 
      });
      observer.observe(sentinel);
    }
  });
</script>