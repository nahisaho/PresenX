# CLAUDE.md - Phase 5: HTML生成（Technical版）

## 🎯 フェーズ概要

**フェーズ名**: HTML生成（技術者版）
**目的**: 最新技術を活用した高性能・高機能なHTMLプレゼンテーションを構築する
**想定時間**: 45-90分
**成果物**: 高度なインタラクティブプレゼンテーション + 技術ドキュメント
**対象者**: 開発者、技術者、最新技術に興味がある人、高度な機能を求める人

## 🚀 Technical版の特徴

### ⚡ 最新技術の活用

**技術スタック**:
- **PWA対応**: Service Worker + Manifest + Offline機能
- **ES6+ JavaScript**: モジュール化、非同期処理、最新言語機能
- **CSS Grid/Flexbox**: 高度なレイアウトシステム
- **WebGL**: 3D図表・アニメーション
- **WebAssembly**: 高性能計算処理
- **Web Components**: 再利用可能なカスタム要素

### 🔧 開発者向け機能

**技術機能**:
- **ホットリロード**: リアルタイム編集・プレビュー
- **モジュール分割**: 機能別ファイル構成
- **TypeScript対応**: 型安全なコード
- **Webpack/Vite**: モダンビルドシステム
- **テスト自動化**: Jest + Cypress
- **CI/CD連携**: GitHub Actions

## 🏗️ 高度なHTML生成アーキテクチャ

### Step 1: モダンプロジェクト構成

#### プロジェクト構造

```
presentation-tech/
├── src/                          # ソースコード
│   ├── components/               # Webコンポーネント
│   │   ├── slides/
│   │   │   ├── TitleSlide.js
│   │   │   ├── ContentSlide.js
│   │   │   └── ChartSlide.js
│   │   ├── charts/
│   │   │   ├── AdvancedChart.js
│   │   │   ├── 3DVisualization.js
│   │   │   └── InteractiveGraph.js
│   │   └── ui/
│   │       ├── ProgressBar.js
│   │       ├── Navigation.js
│   │       └── ControlPanel.js
│   ├── styles/                   # SCSS/CSS
│   │   ├── base/
│   │   ├── components/
│   │   ├── themes/
│   │   └── utils/
│   ├── data/                     # データファイル
│   │   ├── charts-config.json
│   │   ├── animations.json
│   │   └── content.yaml
│   ├── workers/                  # Web Workers
│   │   ├── data-processor.js
│   │   └── render-worker.js
│   └── main.js                   # エントリーポイント
├── public/                       # 静的ファイル
│   ├── manifest.json            # PWAマニフェスト
│   ├── sw.js                    # Service Worker
│   └── icons/
├── tests/                        # テストファイル
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/                         # 技術ドキュメント
│   ├── API.md
│   ├── DEPLOYMENT.md
│   └── DEVELOPMENT.md
├── build/                        # ビルド設定
│   ├── webpack.config.js
│   ├── vite.config.js
│   └── rollup.config.js
├── package.json
├── tsconfig.json
├── jest.config.js
└── cypress.config.js
```

### Step 2: 高度なWebコンポーネント

#### カスタムスライドコンポーネント

**src/components/slides/BaseSlide.js**:
```javascript
class BaseSlide extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' });
        this.animations = [];
        this.interactives = [];
    }

    connectedCallback() {
        this.render();
        this.setupAnimations();
        this.setupInteractivity();
        this.setupAccessibility();
    }

    render() {
        const template = this.getTemplate();
        this.shadowRoot.innerHTML = template;
    }

    getTemplate() {
        return `
            <style>
                :host {
                    display: block;
                    width: 100%;
                    height: 100vh;
                    position: relative;
                    overflow: hidden;
                }
                
                .slide-content {
                    display: grid;
                    grid-template-rows: auto 1fr auto;
                    height: 100%;
                    padding: 2rem;
                    background: var(--slide-background, #ffffff);
                    color: var(--slide-text, #333333);
                }
                
                .slide-header {
                    grid-row: 1;
                    border-bottom: 2px solid var(--primary-color, #007acc);
                    padding-bottom: 1rem;
                    margin-bottom: 2rem;
                }
                
                .slide-main {
                    grid-row: 2;
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                }
                
                .slide-footer {
                    grid-row: 3;
                    display: flex;
                    justify-content: space-between;
                    align-items: center;
                    margin-top: 2rem;
                    padding-top: 1rem;
                    border-top: 1px solid #eee;
                    font-size: 0.8rem;
                    color: #666;
                }
                
                /* アニメーション */
                @keyframes slideInFromLeft {
                    0% { transform: translateX(-100%); opacity: 0; }
                    100% { transform: translateX(0); opacity: 1; }
                }
                
                @keyframes slideInFromRight {
                    0% { transform: translateX(100%); opacity: 0; }
                    100% { transform: translateX(0); opacity: 1; }
                }
                
                @keyframes fadeInUp {
                    0% { transform: translateY(30px); opacity: 0; }
                    100% { transform: translateY(0); opacity: 1; }
                }
                
                .animate-in {
                    animation-duration: 0.6s;
                    animation-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
                    animation-fill-mode: both;
                }
                
                .animate-slide-left { animation-name: slideInFromLeft; }
                .animate-slide-right { animation-name: slideInFromRight; }
                .animate-fade-up { animation-name: fadeInUp; }
            </style>
            
            <div class="slide-content">
                <header class="slide-header">
                    <slot name="header"></slot>
                </header>
                <main class="slide-main">
                    <slot name="content"></slot>
                </main>
                <footer class="slide-footer">
                    <slot name="footer"></slot>
                </footer>
            </div>
        `;
    }

    setupAnimations() {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    this.triggerAnimations();
                }
            });
        });
        observer.observe(this);
    }

    triggerAnimations() {
        const elements = this.shadowRoot.querySelectorAll('[data-animate]');
        elements.forEach((el, index) => {
            setTimeout(() => {
                const animation = el.dataset.animate;
                el.classList.add('animate-in', `animate-${animation}`);
            }, index * 200);
        });
    }

    setupInteractivity() {
        // タッチ・キーボード・マウス操作
        this.addEventListener('touchstart', this.handleTouch.bind(this));
        this.addEventListener('keydown', this.handleKeyboard.bind(this));
        this.addEventListener('click', this.handleClick.bind(this));
    }

    setupAccessibility() {
        this.setAttribute('role', 'main');
        this.setAttribute('tabindex', '0');
        this.setAttribute('aria-label', 'Presentation slide');
    }

    handleTouch(event) {
        // タッチジェスチャー処理
    }

    handleKeyboard(event) {
        // キーボードショートカット処理
    }

    handleClick(event) {
        // クリックイベント処理
    }
}

customElements.define('base-slide', BaseSlide);
```

#### 高度なチャートコンポーネント

**src/components/charts/AdvancedChart.js**:
```javascript
import { Chart, registerables } from 'chart.js';
import { WebGLRenderer } from 'three';

Chart.register(...registerables);

class AdvancedChart extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' });
        this.chart = null;
        this.webglRenderer = null;
        this.animationFrameId = null;
    }

    static get observedAttributes() {
        return ['data-source', 'chart-type', 'animation-style', 'interaction-mode'];
    }

    connectedCallback() {
        this.render();
        this.loadData();
    }

    disconnectedCallback() {
        if (this.chart) this.chart.destroy();
        if (this.webglRenderer) this.webglRenderer.dispose();
        if (this.animationFrameId) cancelAnimationFrame(this.animationFrameId);
    }

    render() {
        this.shadowRoot.innerHTML = `
            <style>
                :host {
                    display: block;
                    width: 100%;
                    height: 400px;
                    position: relative;
                }
                
                .chart-container {
                    width: 100%;
                    height: 100%;
                    position: relative;
                    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
                    border-radius: 12px;
                    padding: 20px;
                    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
                }
                
                .chart-canvas {
                    width: 100%;
                    height: 100%;
                }
                
                .chart-controls {
                    position: absolute;
                    top: 10px;
                    right: 10px;
                    display: flex;
                    gap: 10px;
                }
                
                .control-button {
                    background: rgba(255,255,255,0.2);
                    border: none;
                    border-radius: 6px;
                    padding: 8px 12px;
                    color: white;
                    cursor: pointer;
                    transition: all 0.3s ease;
                }
                
                .control-button:hover {
                    background: rgba(255,255,255,0.3);
                    transform: translateY(-2px);
                }
                
                .loading {
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    height: 100%;
                    color: white;
                    font-size: 1.2em;
                }
                
                .loading::after {
                    content: '';
                    width: 20px;
                    height: 20px;
                    border: 2px solid rgba(255,255,255,0.3);
                    border-top: 2px solid white;
                    border-radius: 50%;
                    animation: spin 1s linear infinite;
                    margin-left: 10px;
                }
                
                @keyframes spin {
                    0% { transform: rotate(0deg); }
                    100% { transform: rotate(360deg); }
                }
            </style>
            
            <div class="chart-container">
                <div class="chart-controls">
                    <button class="control-button" id="play-btn">▶</button>
                    <button class="control-button" id="reset-btn">⟲</button>
                    <button class="control-button" id="3d-btn">🎲</button>
                </div>
                <div class="loading" id="loading">データを読み込み中...</div>
                <canvas class="chart-canvas" id="chart-canvas" style="display: none;"></canvas>
            </div>
        `;

        this.setupControls();
    }

    setupControls() {
        const playBtn = this.shadowRoot.getElementById('play-btn');
        const resetBtn = this.shadowRoot.getElementById('reset-btn');
        const threeDBtn = this.shadowRoot.getElementById('3d-btn');

        playBtn.addEventListener('click', () => this.toggleAnimation());
        resetBtn.addEventListener('click', () => this.resetChart());
        threeDBtn.addEventListener('click', () => this.toggle3D());
    }

    async loadData() {
        try {
            const dataSource = this.getAttribute('data-source');
            const response = await fetch(dataSource);
            const data = await response.json();
            
            this.createChart(data);
            this.hideLoading();
        } catch (error) {
            console.error('データ読み込みエラー:', error);
            this.showError();
        }
    }

    createChart(data) {
        const canvas = this.shadowRoot.getElementById('chart-canvas');
        const ctx = canvas.getContext('2d');
        
        const chartType = this.getAttribute('chart-type') || 'line';
        const animationStyle = this.getAttribute('animation-style') || 'smooth';

        this.chart = new Chart(ctx, {
            type: chartType,
            data: data,
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    title: {
                        display: true,
                        text: data.title || 'Advanced Chart',
                        color: 'white',
                        font: { size: 18, weight: 'bold' }
                    },
                    legend: {
                        labels: { color: 'white' }
                    },
                    tooltip: {
                        backgroundColor: 'rgba(0,0,0,0.8)',
                        titleColor: 'white',
                        bodyColor: 'white',
                        borderColor: 'rgba(255,255,255,0.3)',
                        borderWidth: 1
                    }
                },
                scales: {
                    x: {
                        ticks: { color: 'white' },
                        grid: { color: 'rgba(255,255,255,0.1)' }
                    },
                    y: {
                        ticks: { color: 'white' },
                        grid: { color: 'rgba(255,255,255,0.1)' }
                    }
                },
                animation: {
                    duration: animationStyle === 'fast' ? 500 : 2000,
                    easing: animationStyle === 'smooth' ? 'easeInOutQuart' : 'easeOutBounce'
                },
                interaction: {
                    mode: this.getAttribute('interaction-mode') || 'nearest',
                    intersect: false
                }
            }
        });
    }

    toggleAnimation() {
        const playBtn = this.shadowRoot.getElementById('play-btn');
        if (this.chart.options.animation.duration > 0) {
            this.chart.options.animation.duration = 0;
            playBtn.textContent = '▶';
        } else {
            this.chart.options.animation.duration = 2000;
            playBtn.textContent = '⏸';
            this.chart.update();
        }
    }

    resetChart() {
        if (this.chart) {
            this.chart.reset();
        }
    }

    toggle3D() {
        // WebGL 3D表示の切り替え
        if (!this.webglRenderer) {
            this.init3D();
        } else {
            this.dispose3D();
        }
    }

    init3D() {
        // Three.js による3D可視化の初期化
        // 実装詳細は省略
    }

    dispose3D() {
        if (this.webglRenderer) {
            this.webglRenderer.dispose();
            this.webglRenderer = null;
        }
    }

    hideLoading() {
        this.shadowRoot.getElementById('loading').style.display = 'none';
        this.shadowRoot.getElementById('chart-canvas').style.display = 'block';
    }

    showError() {
        this.shadowRoot.getElementById('loading').innerHTML = '❌ データの読み込みに失敗しました';
    }
}

customElements.define('advanced-chart', AdvancedChart);
```

### Step 3: PWA対応

#### Service Worker実装

**public/sw.js**:
```javascript
const CACHE_NAME = 'presentation-tech-v1.2.0';
const OFFLINE_PAGES = [
    '/',
    '/offline.html',
    '/assets/offline-data.json'
];

const STATIC_ASSETS = [
    '/styles/main.css',
    '/scripts/main.js',
    '/fonts/custom-font.woff2',
    '/icons/icon-192x192.png'
];

// インストール時のキャッシュ
self.addEventListener('install', event => {
    event.waitUntil(
        caches.open(CACHE_NAME)
            .then(cache => {
                console.log('キャッシュを作成中...');
                return cache.addAll([...OFFLINE_PAGES, ...STATIC_ASSETS]);
            })
            .then(() => {
                console.log('キャッシュ作成完了');
                return self.skipWaiting();
            })
    );
});

// アクティベーション時の古いキャッシュ削除
self.addEventListener('activate', event => {
    event.waitUntil(
        caches.keys()
            .then(cacheNames => {
                return Promise.all(
                    cacheNames
                        .filter(cacheName => cacheName !== CACHE_NAME)
                        .map(cacheName => caches.delete(cacheName))
                );
            })
            .then(() => {
                console.log('古いキャッシュを削除完了');
                return self.clients.claim();
            })
    );
});

// フェッチイベントの処理
self.addEventListener('fetch', event => {
    // ネットワーク優先戦略（動的コンテンツ）
    if (event.request.url.includes('/api/')) {
        event.respondWith(networkFirst(event.request));
        return;
    }

    // キャッシュ優先戦略（静的アセット）
    if (event.request.destination === 'image' || 
        event.request.destination === 'style' || 
        event.request.destination === 'script') {
        event.respondWith(cacheFirst(event.request));
        return;
    }

    // HTML: ネットワーク優先、フォールバック
    event.respondWith(networkFirstWithOfflinePage(event.request));
});

// ネットワーク優先戦略
async function networkFirst(request) {
    try {
        const response = await fetch(request);
        if (response.ok) {
            const cache = await caches.open(CACHE_NAME);
            cache.put(request, response.clone());
        }
        return response;
    } catch (error) {
        return caches.match(request);
    }
}

// キャッシュ優先戦略
async function cacheFirst(request) {
    const cached = await caches.match(request);
    if (cached) {
        // バックグラウンドでキャッシュ更新
        fetch(request).then(response => {
            if (response.ok) {
                caches.open(CACHE_NAME).then(cache => {
                    cache.put(request, response);
                });
            }
        });
        return cached;
    }
    return fetch(request);
}

// オフラインページ対応
async function networkFirstWithOfflinePage(request) {
    try {
        return await fetch(request);
    } catch (error) {
        const cached = await caches.match(request);
        if (cached) return cached;
        
        if (request.destination === 'document') {
            return caches.match('/offline.html');
        }
        
        throw error;
    }
}

// バックグラウンドシンク
self.addEventListener('sync', event => {
    if (event.tag === 'presentation-data-sync') {
        event.waitUntil(syncPresentationData());
    }
});

async function syncPresentationData() {
    try {
        // プレゼンテーションデータの同期処理
        const data = await fetch('/api/presentation/sync');
        const cache = await caches.open(CACHE_NAME);
        await cache.put('/api/presentation/data', new Response(JSON.stringify(data)));
        
        // クライアントに通知
        const clients = await self.clients.matchAll();
        clients.forEach(client => {
            client.postMessage({
                type: 'DATA_SYNCED',
                data: data
            });
        });
    } catch (error) {
        console.error('データ同期エラー:', error);
    }
}

// Push通知
self.addEventListener('push', event => {
    const options = {
        body: event.data ? event.data.text() : 'プレゼンテーションが更新されました',
        icon: '/icons/icon-192x192.png',
        badge: '/icons/badge-72x72.png',
        vibrate: [100, 50, 100],
        data: {
            dateOfArrival: Date.now(),
            primaryKey: 1
        },
        actions: [
            {
                action: 'explore',
                title: '表示',
                icon: '/icons/checkmark.png'
            },
            {
                action: 'close',
                title: '閉じる',
                icon: '/icons/xmark.png'
            }
        ]
    };

    event.waitUntil(
        self.registration.showNotification('PrezenX通知', options)
    );
});
```

#### PWAマニフェスト

**public/manifest.json**:
```json
{
    "name": "PrezenX Technical Presentation",
    "short_name": "PrezenX Tech",
    "description": "高度な技術機能を備えたプレゼンテーションアプリ",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#1a1a1a",
    "theme_color": "#007acc",
    "orientation": "landscape-primary",
    "categories": ["productivity", "business", "education"],
    "lang": "ja",
    "dir": "ltr",
    "icons": [
        {
            "src": "/icons/icon-72x72.png",
            "sizes": "72x72",
            "type": "image/png",
            "purpose": "any maskable"
        },
        {
            "src": "/icons/icon-96x96.png",
            "sizes": "96x96",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-128x128.png",
            "sizes": "128x128",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-144x144.png",
            "sizes": "144x144",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-152x152.png",
            "sizes": "152x152",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-192x192.png",
            "sizes": "192x192",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-384x384.png",
            "sizes": "384x384",
            "type": "image/png",
            "purpose": "any"
        },
        {
            "src": "/icons/icon-512x512.png",
            "sizes": "512x512",
            "type": "image/png",
            "purpose": "any"
        }
    ],
    "screenshots": [
        {
            "src": "/screenshots/desktop-1.png",
            "sizes": "1280x720",
            "type": "image/png",
            "platform": "wide"
        },
        {
            "src": "/screenshots/mobile-1.png",
            "sizes": "390x844",
            "type": "image/png"
        }
    ],
    "shortcuts": [
        {
            "name": "新しいプレゼンを開始",
            "short_name": "新規作成",
            "description": "新しいプレゼンテーションを作成します",
            "url": "/new",
            "icons": [{ "src": "/icons/new-96x96.png", "sizes": "96x96" }]
        },
        {
            "name": "最近のプレゼン",
            "short_name": "履歴",
            "description": "最近使用したプレゼンテーションを表示します",
            "url": "/recent",
            "icons": [{ "src": "/icons/recent-96x96.png", "sizes": "96x96" }]
        }
    ],
    "share_target": {
        "action": "/share",
        "method": "POST",
        "enctype": "multipart/form-data",
        "params": {
            "title": "title",
            "text": "text",
            "url": "url",
            "files": [
                {
                    "name": "files",
                    "accept": ["text/markdown", ".md", "application/json"]
                }
            ]
        }
    }
}
```

### Step 4: TypeScript + モダンビルドシステム

#### TypeScript設定

**tsconfig.json**:
```json
{
    "compilerOptions": {
        "target": "ES2022",
        "module": "ESNext",
        "moduleResolution": "node",
        "lib": ["ES2022", "DOM", "DOM.Iterable", "WebWorker"],
        "allowJs": true,
        "outDir": "./dist",
        "rootDir": "./src",
        "strict": true,
        "esModuleInterop": true,
        "skipLibCheck": true,
        "forceConsistentCasingInFileNames": true,
        "declaration": true,
        "declarationMap": true,
        "sourceMap": true,
        "removeComments": false,
        "noEmitOnError": true,
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true,
        "resolveJsonModule": true,
        "isolatedModules": true,
        "noUncheckedIndexedAccess": true,
        "exactOptionalPropertyTypes": true,
        "noImplicitReturns": true,
        "noFallthroughCasesInSwitch": true,
        "noUncheckedIndexedAccess": true,
        "allowUnreachableCode": false,
        "allowUnusedLabels": false,
        "paths": {
            "@/*": ["./src/*"],
            "@components/*": ["./src/components/*"],
            "@utils/*": ["./src/utils/*"],
            "@types/*": ["./src/types/*"]
        }
    },
    "include": [
        "src/**/*",
        "tests/**/*"
    ],
    "exclude": [
        "node_modules",
        "dist",
        "build"
    ]
}
```

#### Vite設定

**vite.config.js**:
```javascript
import { defineConfig } from 'vite';
import { resolve } from 'path';

export default defineConfig({
    root: 'src',
    build: {
        outDir: '../dist',
        emptyOutDir: true,
        rollupOptions: {
            input: {
                main: resolve(__dirname, 'src/index.html'),
                offline: resolve(__dirname, 'src/offline.html')
            }
        },
        target: 'es2022',
        minify: 'terser',
        terserOptions: {
            compress: {
                drop_console: true,
                drop_debugger: true
            }
        },
        sourcemap: true,
        chunkSizeWarningLimit: 1000
    },
    server: {
        port: 3000,
        hot: true,
        cors: true
    },
    preview: {
        port: 4000,
        cors: true
    },
    plugins: [
        // PWA plugin
        {
            name: 'pwa',
            configureServer(server) {
                server.middlewares.use('/sw.js', (req, res, next) => {
                    res.setHeader('Content-Type', 'application/javascript');
                    next();
                });
            }
        }
    ],
    resolve: {
        alias: {
            '@': resolve(__dirname, 'src'),
            '@components': resolve(__dirname, 'src/components'),
            '@utils': resolve(__dirname, 'src/utils'),
            '@types': resolve(__dirname, 'src/types')
        }
    },
    css: {
        preprocessorOptions: {
            scss: {
                additionalData: `@import "@/styles/variables.scss";`
            }
        }
    },
    optimizeDeps: {
        include: ['reveal.js', 'chart.js', 'three', 'mermaid']
    }
});
```

## 🗣️ Claude Code協働方針（Technical版）

### このフェーズでClaude Codeに期待すること

1. **技術プレゼンテーションの特化機能**
   - コードハイライト、ライブコーディング環境の実装
   - アーキテクチャ図、システム構成図の美しい表示
   - APIドキュメント、技術仕様書の効果的な可視化
   - デモ・インタラクティブ要素の効果的な統合

2. **開発者体験の最適化**
   - 技術者が直感的に理解できるインターフェース
   - コードの読みやすさ、コピーの容易さを重視
   - 技術的な詳細と全体像のバランス調整
   - ハンズオン・デモに適したインタラクティブ性

3. **技術コミュニティ標準への適合**
   - オープンソースコミュニティのベストプラクティス
   - 技術カンファレンス・勉強会での発表品質
   - 最新技術トレンドへの対応
   - 技術デモの安定性・再現性確保

### 積極的に相談したいポイント

- [ ] 「技術者が求めるレベルの詳細さか？」
- [ ] 「コード・アーキテクチャが理解しやすいか？」
- [ ] 「ライブデモ・インタラクティブ要素が効果的か？」
- [ ] 「技術カンファレンスレベルの品質か？」
- [ ] 「開発者コミュニティで受け入れられるか？」
- [ ] 「デモ・ハンズオンがスムーズに実行できるか？」
- [ ] 「技術的な正確性・信頼性は十分か？」

## 🔧 高度な品質保証

### 自動テスト環境

#### Jest単体テスト

**tests/unit/components/BaseSlide.test.js**:
```javascript
import { jest, describe, it, expect, beforeEach, afterEach } from '@jest/globals';
import { JSDOM } from 'jsdom';

// DOM環境のセットアップ
const dom = new JSDOM('<!DOCTYPE html><html><body></body></html>');
global.window = dom.window;
global.document = dom.window.document;
global.HTMLElement = dom.window.HTMLElement;
global.customElements = dom.window.customElements;

// BaseSlideコンポーネントのインポート
import '../../../src/components/slides/BaseSlide.js';

describe('BaseSlide Component', () => {
    let slideElement;

    beforeEach(() => {
        slideElement = document.createElement('base-slide');
        document.body.appendChild(slideElement);
    });

    afterEach(() => {
        document.body.removeChild(slideElement);
    });

    it('should render with shadow DOM', () => {
        expect(slideElement.shadowRoot).toBeTruthy();
        expect(slideElement.shadowRoot.querySelector('.slide-content')).toBeTruthy();
    });

    it('should setup accessibility attributes', () => {
        expect(slideElement.getAttribute('role')).toBe('main');
        expect(slideElement.getAttribute('tabindex')).toBe('0');
        expect(slideElement.getAttribute('aria-label')).toBe('Presentation slide');
    });

    it('should handle animations correctly', (done) => {
        const animatedElement = document.createElement('div');
        animatedElement.setAttribute('data-animate', 'fade-up');
        slideElement.shadowRoot.querySelector('.slide-main').appendChild(animatedElement);

        slideElement.triggerAnimations();

        setTimeout(() => {
            expect(animatedElement.classList.contains('animate-in')).toBe(true);
            expect(animatedElement.classList.contains('animate-fade-up')).toBe(true);
            done();
        }, 100);
    });

    it('should respond to keyboard events', () => {
        const handleKeyboardSpy = jest.spyOn(slideElement, 'handleKeyboard');
        
        const event = new dom.window.KeyboardEvent('keydown', { 
            key: 'ArrowRight',
            bubbles: true 
        });
        
        slideElement.dispatchEvent(event);
        expect(handleKeyboardSpy).toHaveBeenCalledWith(event);
    });
});
```

#### Cypress E2Eテスト

**tests/e2e/presentation.cy.js**:
```javascript
describe('Presentation E2E Tests', () => {
    beforeEach(() => {
        cy.visit('http://localhost:3000');
    });

    it('should load presentation successfully', () => {
        cy.get('base-slide').should('be.visible');
        cy.get('.slide-content').should('exist');
    });

    it('should navigate between slides using keyboard', () => {
        cy.get('body').type('{rightarrow}');
        cy.get('[data-slide-index="1"]').should('be.visible');
        
        cy.get('body').type('{leftarrow}');
        cy.get('[data-slide-index="0"]').should('be.visible');
    });

    it('should render charts correctly', () => {
        cy.get('advanced-chart').should('be.visible');
        cy.get('canvas').should('exist');
        
        // チャートデータの読み込み待機
        cy.get('.loading', { timeout: 10000 }).should('not.exist');
        cy.get('canvas').should('be.visible');
    });

    it('should work offline', () => {
        // Service Workerの登録待機
        cy.window().then((win) => {
            return win.navigator.serviceWorker.ready;
        });

        // オフラインモードのシミュレーション
        cy.window().then((win) => {
            win.navigator.serviceWorker.controller.postMessage({
                command: 'SIMULATE_OFFLINE'
            });
        });

        cy.reload();
        cy.get('.offline-indicator').should('be.visible');
        cy.get('base-slide').should('be.visible');
    });

    it('should be responsive on mobile', () => {
        cy.viewport('iphone-x');
        
        cy.get('base-slide').should('be.visible');
        cy.get('.slide-content').should('have.css', 'padding', '15px');
        
        // タッチナビゲーション
        cy.get('base-slide').trigger('touchstart', { touches: [{ clientX: 100, clientY: 100 }] });
        cy.get('base-slide').trigger('touchend', { touches: [{ clientX: 50, clientY: 100 }] });
    });

    it('should have proper accessibility', () => {
        cy.injectAxe();
        cy.checkA11y();
        
        // キーボードナビゲーション
        cy.get('base-slide').focus();
        cy.focused().should('have.attr', 'role', 'main');
        
        // スクリーンリーダー対応
        cy.get('base-slide').should('have.attr', 'aria-label');
    });

    it('should perform well', () => {
        cy.window().then((win) => {
            const performance = win.performance;
            const navigationTiming = performance.getEntriesByType('navigation')[0];
            
            expect(navigationTiming.loadEventEnd - navigationTiming.navigationStart).to.be.below(3000);
        });
    });
});
```

### パフォーマンス監視

#### Web Vitals測定

**src/utils/performance.js**:
```javascript
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals';

class PerformanceMonitor {
    constructor() {
        this.metrics = new Map();
        this.observers = [];
        this.initializeMonitoring();
    }

    initializeMonitoring() {
        // Core Web Vitals
        getCLS(this.recordMetric.bind(this, 'CLS'));
        getFID(this.recordMetric.bind(this, 'FID'));
        getFCP(this.recordMetric.bind(this, 'FCP'));
        getLCP(this.recordMetric.bind(this, 'LCP'));
        getTTFB(this.recordMetric.bind(this, 'TTFB'));

        // カスタムメトリクス
        this.measureSlideTransitionTime();
        this.measureChartRenderTime();
        this.measureMemoryUsage();
    }

    recordMetric(name, metric) {
        this.metrics.set(name, metric);
        console.log(`${name}:`, metric.value);

        // パフォーマンス警告
        this.checkThresholds(name, metric.value);
        
        // 分析サービスに送信（本番環境）
        if (process.env.NODE_ENV === 'production') {
            this.sendToAnalytics(name, metric);
        }
    }

    checkThresholds(name, value) {
        const thresholds = {
            'CLS': 0.1,      // Good: ≤ 0.1
            'FID': 100,      // Good: ≤ 100ms
            'LCP': 2500,     // Good: ≤ 2.5s
            'FCP': 1800,     // Good: ≤ 1.8s
            'TTFB': 800      // Good: ≤ 800ms
        };

        if (thresholds[name] && value > thresholds[name]) {
            console.warn(`⚠️ ${name} (${value}) exceeds threshold (${thresholds[name]})`);
            this.suggestOptimizations(name, value);
        }
    }

    suggestOptimizations(metric, value) {
        const suggestions = {
            'CLS': [
                'レイアウトシフトを避けるため、画像・動画にサイズ属性を設定',
                'Webフォントの読み込み最適化',
                'Dynamic import の使用を検討'
            ],
            'FID': [
                'JavaScriptバンドルサイズの削減',
                'Code splitting の実装',
                'Web Workers の活用'
            ],
            'LCP': [
                'プリロード・プリコネクトの活用',
                '画像最適化・次世代フォーマット使用',
                'CDN の活用'
            ]
        };

        if (suggestions[metric]) {
            console.group(`🔧 ${metric} 最適化提案:`);
            suggestions[metric].forEach(suggestion => console.log(`• ${suggestion}`));
            console.groupEnd();
        }
    }

    measureSlideTransitionTime() {
        const observer = new PerformanceObserver((list) => {
            list.getEntries().forEach((entry) => {
                if (entry.name.includes('slide-transition')) {
                    this.recordMetric('SlideTransition', { value: entry.duration });
                }
            });
        });
        observer.observe({ entryTypes: ['measure'] });
        this.observers.push(observer);
    }

    measureChartRenderTime() {
        const observer = new PerformanceObserver((list) => {
            list.getEntries().forEach((entry) => {
                if (entry.name.includes('chart-render')) {
                    this.recordMetric('ChartRender', { value: entry.duration });
                }
            });
        });
        observer.observe({ entryTypes: ['measure'] });
        this.observers.push(observer);
    }

    measureMemoryUsage() {
        if ('memory' in performance) {
            setInterval(() => {
                const memory = performance.memory;
                this.recordMetric('MemoryUsage', {
                    value: memory.usedJSHeapSize,
                    total: memory.totalJSHeapSize,
                    limit: memory.jsHeapSizeLimit
                });
            }, 30000); // 30秒ごと
        }
    }

    sendToAnalytics(name, metric) {
        // Google Analytics、Datadog、などへの送信
        if (window.gtag) {
            window.gtag('event', name, {
                event_category: 'Web Vitals',
                value: Math.round(metric.value),
                metric_id: metric.id,
                metric_value: metric.value,
                metric_delta: metric.delta
            });
        }
    }

    getReport() {
        const report = {};
        this.metrics.forEach((value, key) => {
            report[key] = value;
        });
        return report;
    }

    dispose() {
        this.observers.forEach(observer => observer.disconnect());
        this.observers = [];
        this.metrics.clear();
    }
}

export const performanceMonitor = new PerformanceMonitor();
```

## ✅ Technical版完了チェックリスト

### 技術実装確認
- [ ] TypeScriptコンパイルエラーなし
- [ ] ESLint・Prettierチェック通過
- [ ] 単体テスト（Jest）100%パス
- [ ] E2Eテスト（Cypress）全シナリオ通過
- [ ] バンドルサイズ最適化（<500KB gzipped）
- [ ] Web Vitals すべて Good 範囲内

### PWA機能確認
- [ ] Service Worker正常動作
- [ ] オフライン機能完全動作
- [ ] マニフェスト検証通過
- [ ] プッシュ通知動作確認
- [ ] インストール可能性確認

### セキュリティ確認
- [ ] CSP（Content Security Policy）設定
- [ ] XSS対策実装
- [ ] HTTPS対応確認
- [ ] セキュリティヘッダー設定
- [ ] 脆弱性スキャン実施

### パフォーマンス確認
- [ ] Lighthouse スコア 90+ (全項目)
- [ ] Core Web Vitals すべて Green
- [ ] メモリリーク検査通過
- [ ] 長時間動作テスト完了
- [ ] 負荷テスト実施

### ブラウザ互換性確認
- [ ] Chrome/Edge/Firefox/Safari 最新版
- [ ] モバイルブラウザ対応確認
- [ ] WebGL対応ブラウザでの3D機能確認
- [ ] Progressive Enhancement 確認

## 🚀 Technical版の技術的優位性

### 🔬 最先端技術の活用
- **Web Components**: 標準技術による高い互換性
- **PWA**: アプリライクな体験とオフライン対応
- **WebGL**: ハードウェア加速による高性能3D表示
- **Web Workers**: メインスレッドをブロックしない処理
- **ES2022+**: 最新言語機能による開発効率向上

### ⚡ 圧倒的なパフォーマンス
- **Code Splitting**: 必要な機能のみ読み込み
- **Tree Shaking**: 未使用コードの自動除去
- **Lazy Loading**: 遅延読み込みによる高速化
- **Service Worker**: 積極的キャッシング戦略
- **WebAssembly**: 計算集約的処理の高速化

### 🛡️ エンタープライズグレードの品質
- **TypeScript**: 型安全性による開発品質向上
- **自動テスト**: 包括的なテスト環境
- **パフォーマンス監視**: リアルタイム品質管理
- **セキュリティ**: 最新のセキュリティベストプラクティス
- **アクセシビリティ**: WCAG準拠の高いアクセシビリティ

---

**🤖 Claude Codeへの指示（Technical版）**:
このTechnical版では、最新のWeb技術を積極的に活用し、エンタープライズレベルの品質と性能を実現してください。技術的な挑戦を恐れず、将来性と拡張性を重視した実装をお願いします。ただし、Over Engineering にならないよう、実用性とのバランスを保ってください。