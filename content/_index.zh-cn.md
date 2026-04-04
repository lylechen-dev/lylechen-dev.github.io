---
title: "欢迎来到 Blowfish! :tada:"
description: "此页面是使用 Hugo 的 Blowfish 主题搭建的"
---




<div id="friends-links" role="list" aria-label="友链列表"></div>

<style>
/* 友链网格布局 */
#friends-links {
  margin: 20px 0;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 220px), 1fr));
  gap: 14px;
  contain: layout;
}

/* 浅色模式 */
.friend-card {
  padding: 16px 18px;
  background: rgba(var(--color-neutral), 0.6);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-radius: 10px;
  border: 1px solid rgba(var(--color-neutral-200), 0.5);
  text-decoration: none;
  color: rgba(var(--color-neutral-800), 1);
  display: flex;
  align-items: center;
  gap: 12px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.05);
  transform: translateY(0);
  transition: 
    background 0.25s ease,
    box-shadow 0.25s ease,
    transform 0.25s ease,
    border-color 0.25s ease;
  position: relative;
  overflow: hidden;
}

/* 顶部渐变条效果 */
.friend-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, #5dc1d9 0%, #389bb0 50%, #5dc1d9 100%);
  transform: translateX(-100%);
  transition: transform 0.3s ease-out;
  z-index: 1;
}

.friend-card:hover {
  background: rgba(93, 193, 217, 0.06);
  border-color: rgba(93, 193, 217, 0.2);
  box-shadow: 
    0 4px 12px rgba(93, 193, 217, 0.08),
    0 2px 6px rgba(0, 0, 0, 0.08);
  transform: translateY(-4px);
}

.friend-card:hover::before {
  transform: translateX(0);
}

.friend-card:focus-visible {
  outline: none;
  box-shadow: 
    0 0 0 3px rgba(93, 193, 217, 0.2),
    0 6px 16px rgba(93, 193, 217, 0.1),
    0 2px 8px rgba(0, 0, 0, 0.1);
  background: rgba(93, 193, 217, 0.06);
  transform: translateY(-4px);
}

.friend-card:active {
  transform: translateY(-1px);
  transition-duration: 0.1s;
}

/* 深色模式 */
html.dark .friend-card,
.dark .friend-card {
  background: rgba(var(--color-neutral-800), 0.6);
  border: 1px solid rgba(var(--color-neutral-700), 0.5);
  color: rgba(var(--color-neutral-200), 1);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

html.dark .friend-card:hover,
.dark .friend-card:hover {
  background: rgba(93, 193, 217, 0.1);
  border-color: rgba(93, 193, 217, 0.3);
  box-shadow: 
    0 4px 12px rgba(93, 193, 217, 0.12),
    0 2px 6px rgba(0, 0, 0, 0.15);
  transform: translateY(-4px);
}

html.dark .friend-card:focus-visible,
.dark .friend-card:focus-visible {
  outline: none;
  box-shadow: 
    0 0 0 3px rgba(93, 193, 217, 0.2),
    0 6px 16px rgba(93, 193, 217, 0.15),
    0 2px 8px rgba(0, 0, 0, 0.2);
  background: rgba(93, 193, 217, 0.1);
  transform: translateY(-4px);
}

html.dark .friend-card:active,
.dark .friend-card:active {
  transform: translateY(-1px);
}

/* logo 样式 - 增强效果 */
.card-logo {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  object-fit: cover;
  flex-shrink: 0;
  border: 2px solid transparent;
  transition: 
    transform 0.3s ease,
    box-shadow 0.25s ease,
    border-color 0.25s ease;
  position: relative;
  z-index: 2;
}

.friend-card:hover .card-logo {
  transform: scale(1.08);
  border-color: #5dc1d9;
  box-shadow: 
    0 0 0 3px rgba(93, 193, 217, 0.08),
    0 3px 8px rgba(93, 193, 217, 0.1);
}

.friend-card:focus-visible .card-logo {
  transform: scale(1.06);
  box-shadow: 0 0 0 3px rgba(93, 193, 217, 0.2);
}

/* 文字容器 */
.card-text {
  flex: 1;
  position: relative;
  z-index: 2;
}

.friend-name {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 4px;
  color: inherit;
  transition: color 0.25s ease;
  display: inline-block;
}

.friend-card:hover .friend-name {
  color: #5dc1d9;
}

.friend-desc {
  font-size: 13px;
  line-height: 1.3;
  opacity: 0.85;
  color: inherit;
  transition: 
    opacity 0.25s ease;
}

.friend-card:hover .friend-desc {
  opacity: 1;
}

html.dark .friend-card:hover .friend-name,
.dark .friend-card:hover .friend-name {
  color: #5dc1d9;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function () {
  const links = [
    { name: "云泽の小屋", desc: "最好的朋友，他的博客是世界上最详细网络安全实践笔记！", url: "https://zeyun.org", logo: "https://zeyun.org/media/website/Happy_Mac.png" },
    { name: "猪老师在线", desc: "最有能力的老师，网络安全没人比他讲的更好！", url: "https://www.pigteacher.com", logo: "https://www.pigteacher.com/wp-content/uploads/2025/01/cropped-1-180x180.jpg" },
    { name: "云泽の小屋-网站推荐", desc: "优秀网站的收藏夹", url: "https://zeyun.org/good_web.html", logo: "https://zeyun.org/media/website/Happy_Mac.png" },
    { name: "Quick Reference", desc: "自己部署的Quick Reference镜像站，感觉里面东西速查挺方便的", url: "https://ref.lylesta.dpdns.org:8443/", logo: "https://ref.lylesta.dpdns.org:8443/icons/touch-icon-iphone-retina.png" }
  ];

  const container = document.getElementById("friends-links");

  links.forEach(item => {
    const card = document.createElement('a');
    card.className = "friend-card";
    card.href = item.url;
    card.target = "_blank";
    card.rel = "noopener noreferrer";
    card.setAttribute('role', 'listitem');
    card.setAttribute('aria-label', `访问 ${item.name} - ${item.desc}`);
    
    card.innerHTML = `
      <img src="${item.logo}" class="card-logo" alt="${item.name} logo" loading="lazy" onerror="this.style.display='none'">
      <div class="card-text">
        <div class="friend-name">${item.name}</div>
        <div class="friend-desc">${item.desc}</div>
      </div>
    `;
    container.appendChild(card);
  });

  // 监听主题切换，重置颜色
  const observer = new MutationObserver(() => {
    document.querySelectorAll('.friend-card').forEach(card => {
      card.style.color = '';
    });
  });
  observer.observe(document.documentElement, { 
    attributes: true, 
    attributeFilter: ['class'] 
  });
});
</script>