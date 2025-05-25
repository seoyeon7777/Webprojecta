# Webprojecta
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>한글 겸용 Type Writer</title>
  <style>
    button {
      width: 40px;
      height: 40px;
      margin: 2px;
      font-size: 16px;
      cursor: pointer;
    }

    .group1 button { background-color: #f8b195; }
    .group2 button { background-color: #f67280; }
    .group3 button { background-color: #c06c84; }
    .group4 button { background-color: #6c5b7b; }

    .glow {
      background-color: yellow !important;
    }
  </style>
</head>
<body>
  <h1>제작자: 방서연 | 학번: 2402176 | 소속: 한양 빅데이터</h1>

  <div class="display" id="display"></div>

  <div class="keyboard">
    <!-- 숫자열 -->
    <div class="row group1">
      <button>1</button><button>2</button><button>3</button>
      <button>4</button><button>5</button><button>6</button>
      <button>7</button><button>8</button><button>9</button>
      <button>0</button>
    </div>

    <!-- 영문자 -->
    <div class="row group2">
      <button>q</button><button>w</button><button>e</button>
      <button>r</button><button>t</button><button>y</button>
      <button>u</button><button>i</button><button>o</button>
      <button>p</button>
    </div>

    <div class="row group3">
      <button>a</button><button>s</button><button>d</button>
      <button>f</button><button>g</button><button>h</button>
      <button>j</button><button>k</button><button>l</button>
    </div>

    <div class="row group4">
      <button>z</button><button>x</button><button>c</button>
      <button>v</button><button>b</button><button>n</button>
      <button>m</button><button>,</button><button>.</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");
    let isKorean = false;

    document.addEventListener("keydown", function(e) {
      let key = e.key.toLowerCase();

      if (key === '.') {
        toggleLanguage();
        return;
      }

      if (key.length === 1) {
        const char = isKorean ? toKorean(key) : key;
        display.textContent += char;
        flashKey(key);
      }
    });

    function flashKey(key) {
      const buttons = document.querySelectorAll("button");
      buttons.forEach(btn => {
        if (btn.textContent.toLowerCase() === key) {
          btn.classList.add("glow");
          setTimeout(() => btn.classList.remove("glow"), 150);
        }
      });
    }

    function toggleLanguage() {
      isKorean = !isKorean;
      alert(isKorean ? "한글 입력 모드" : "영문 입력 모드");
    }

    function toKorean(char) {
      const korMap = {
        q: "ㅂ", w: "ㅈ", e: "ㄷ", r: "ㄱ", t: "ㅅ",
        y: "ㅛ", u: "ㅕ", i: "ㅑ", o: "ㅐ", p: "ㅔ",
        a: "ㅁ", s: "ㄴ", d: "ㅇ", f: "ㄹ", g: "ㅎ",
        h: "ㅗ", j: "ㅓ", k: "ㅏ", l: "ㅣ",
        z: "ㅋ", x: "ㅌ", c: "ㅊ", v: "ㅍ", b: "ㅠ",
        n: "ㅜ", m: "ㅡ",
        "1": "1", "2": "2", "3": "3", "4": "4", "5": "5",
        "6": "6", "7": "7", "8": "8", "9": "9", "0": "0",
        ",": ",", ".": "."
      };
      return korMap[char] || char;
    }
  </script>
</body>
</html>
