<meta charset="utf-8"/>

> ## 🌸 이 Fork에서 바뀐 점 (오픈소스SW 개론 과제: OSS Playground Hunter)
>
> **실행해 보기:** https://yubin0114.github.io/sandspiel/ · 원본: [MaxBittker/sandspiel](https://github.com/MaxBittker/sandspiel) (MIT License, 아래 LICENSE 유지)
>
> | 수정 | 파일 | 변경 내용 |
> |---|---|---|
> | 분홍 모래 | `js/glsl/sand.glsl` | 모래 색상 `hue = 0.1`(베이지) → `0.9`(분홍) |
> | 위로 떨어지는 모래 | `crate/src/species.rs` | `update_sand`가 아래 칸(dy=+1) 대신 위 칸(dy=-1)을 확인하고 그쪽으로 이동 → 모래가 천장에 거꾸로 쌓임 |
> | GitHub Pages 배포 | `.github/workflows/pages.yml`, `webpack.config.js`, `js/app.js`, `index.html`, `js/index.js` | Actions 자동 빌드, `/sandspiel/` 하위 경로 지원, Fork의 오류가 원작자 Sentry로 보고되지 않게 차단 |
>
> 원본과의 전체 차이: [MaxBittker:master...yubin0114:master](https://github.com/MaxBittker/sandspiel/compare/master...yubin0114:sandspiel:master)
> 한계: 로그인, 업로드, 갤러리(Browse)는 원작자의 Firebase에 연결돼 있어 이 배포본에서는 동작하지 않습니다.

# sandspiel

"Imagine the cool phenomenon when the wind blows the falling leaves. This game simulates the phenomenon with powder (dots)!" -DAN-BALL

![](Screenshot.png)

This is a [falling sand](https://en.wikipedia.org/wiki/Falling-sand_game) game built in rust (via wasm), webgl, and some JS glueing things together.

You can [play online](https://sandspiel.club) or read [a longer post on the project](https://maxbittker.com/making-sandspiel)

The goal was to produce an cellular automata environment that's interesting to play with and supports the sharing and forking of fun creations with other players.
Ultimately, I want the platform to support editing and uploading of your own elements via a programmable cellular automata API.

### 🛠️ Build:

```
# build the wasm once:
cd crate && wasm-pack build && cd ..;
npm install;
npm run start;

# then in a separate terminal:
cargo watch -s 'wasm-pack build'
```

a successor to my previous efforts in [javascript](https://github.com/MaxBittker/dust) and [lua](https://github.com/MaxBittker/sand-toy)

Fluid simulation code adopted from
https://github.com/PavelDoGreat/WebGL-Fluid-Simulation
