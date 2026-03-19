---
title: "欢迎来到 Blowfish! :tada:"
description: "此页面是使用 Hugo 的 Blowfish 主题搭建的"
---

<!-- <div id="typing-text" style="background-color: transparent; min-height: 1.5em; font-size: 18px; font-weight: bold; text-align: left;"></div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  const message = "致我们：\n愿我们都能在各自感兴趣的事情上找到更好的自己！\n\n尘.";
  const element = document.getElementById("typing-text");
  let index = 0;

  // 光标
  const cursor = document.createElement('span');
  cursor.classList.add('typing-cursor');
  cursor.textContent = '|';
  element.appendChild(cursor);

  // 光标样式
  const style = document.createElement('style');
  style.textContent = `
    .typing-cursor {
      opacity: 1;
      animation: blink 1s infinite;
      margin-left: 2px;
    }
    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }
  `;
  document.head.appendChild(style);

  function typeWriter() {
    if (index < message.length) {
      const currentChar = message.charAt(index);

      if (currentChar === '\n') {
        const br = document.createElement('br');
        element.insertBefore(br, cursor);
      } else {
        const char = document.createTextNode(currentChar);
        element.insertBefore(char, cursor);
      }

      index++;
      setTimeout(typeWriter, 150);
    } else {
      // 结束后隐藏光标
      cursor.style.animation = 'none';
      cursor.style.opacity = '0';
    }
  }

  setTimeout(typeWriter, 500);
});
</script> -->

<div id="friends-links" style="margin: 20px 0; display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 16px;"></div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  // 友链数据（自己替换 logo 地址）
  const links = [
    { name: "云泽の小屋", desc: "最好的朋友，他的博客是世界上最详细网络安全实践笔记！", url: "https://zeyun.dpdns.org", logo: "https://zeyun.dpdns.org/media/website/Happy_Mac.png" },
    { name: "猪老师在线", desc: "最有趣的老师，网络安全没人比他讲的更好！", url: "https://www.pigteacher.com", logo: "https://www.pigteacher.com/wp-content/uploads/2025/01/cropped-1-180x180.jpg" },
    { name: "云泽の小屋-网站推荐", desc: "优秀网站的收藏夹", url: "https://zeyun.dpdns.org/good_web.html", logo: "https://zeyun.dpdns.org/media/website/Happy_Mac.png" },
    // { name: "旅行日记", desc: "走遍山川湖海", url: "#", logo: "https://via.placeholder.com/32" },
    // { name: "阅读空间", desc: "文字与思想的旅途", url: "#", logo: "https://via.placeholder.com/32" },
    // { name: "摄影集", desc: "定格每一刻温柔", url: "#", logo: "https://via.placeholder.com/32" }
  ];

  const container = document.getElementById("friends-links");

  // 样式：完全保留你原来的！只加了最外层布局
  const style = document.createElement('style');
  style.textContent = `
    /* 浅色模式 */
    .friend-card {
      padding: 20px;
      background: rgba(255, 255, 255, 0.6);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-radius: 10px;
      border: 1px solid rgba(0, 0, 0, 0.05);
      transition: 0.2s ease;
      text-decoration: none;
      color: #111827;
      /* 关键：图片 + 文字 横向排列 */
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .friend-card:hover {
      background: rgba(255, 255, 255, 0.8);
    }

    /* 深色模式 */
    html.dark .friend-card,
    .dark .friend-card {
      background: rgba(30, 30, 32, 0.6);
      border: 1px solid rgba(255, 255, 255, 0.05);
      color: #f3f4f6;
    }
    html.dark .friend-card:hover,
    .dark .friend-card:hover {
      background: rgba(40, 40, 42, 0.75);
    }

    /* logo 样式 */
    .card-logo {
      width: 32px;
      height: 32px;
      border-radius: 6px;
      object-fit: cover;
      flex-shrink: 0;
    }

    /* 文字容器 */
    .card-text {
      flex: 1;
    }

    .friend-name {
      font-size: 16px;
      font-weight: 600;
      margin-bottom: 6px;
      color: inherit;
    }
    .friend-desc {
      font-size: 13px;
      line-height: 1.4;
      opacity: 0.85;
      color: inherit;
    }
  `;
  document.head.appendChild(style);

  // 生成卡片（只加logo，其余完全不变）
  links.forEach(item => {
    const card = document.createElement('a');
    card.className = "friend-card";
    card.href = item.url;
    card.target = "_blank";
    card.rel = "noopener noreferrer";

    card.innerHTML = `
      <!-- logo 在最左侧，文字整体在右侧 -->
      <img src="${item.logo}" class="card-logo">
      <div class="card-text">
        <div class="friend-name">${item.name}</div>
        <div class="friend-desc">${item.desc}</div>
      </div>
    `;
    container.appendChild(card);
  });

  // 监听主题切换
  const observer = new MutationObserver(() => {
    document.querySelectorAll('.friend-card').forEach(c => c.style.color = '');
  });
  observer.observe(document.documentElement, { attributes: true, attributeFilter: ['class'] });
});
</script>

