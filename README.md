# Kok Input Filter 🚀
<div align="left">
  <img src="https://img.shields.io/badge/version-1.0.0-blue.svg" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License">
  <img src="https://img.shields.io/badge/language-JavaScript-yellow.svg" alt="Language">
</div>

<br>

> **입력 중 실시간 필터링**과 **포커스 아웃(blur) 시 유효성 검증**을 표준 이벤트 기반으로 처리하는 초경량 Vanilla JS 라이브러리입니다.

![Demo GIF](https://github.com/user-attachments/assets/a91423c5-699b-46d6-98e1-655644be8e23)

<img width="800" height="502" alt="image" src="https://github.com/user-attachments/assets/f946735a-bea8-4906-9306-1c8f6f605a15" />

<br>
<br>

## ⚡ Quick Start
별도의 빌드 과정 없이 CDN을 통해 즉시 시작하세요.
```html
<script src="https://cdn.jsdelivr.net/gh/attickok/kok-input-filter@main/kok-input-filter.js"></script>

<input type="text" id="intField" placeholder="숫자만 입력">

<script>
    new KokInputFilter("#intField", { type: "int" });
</script>
```

<br>
<br>

## ✨ Key Features
* **Dual Action**: 실시간 필터링(`input`)과 형식 검증(`blur`)의 완벽한 분리.
* **Event-Driven**: 표준 `CustomEvent`(`success`/`error`)로 UI와 로직을 깔끔하게 분리.
* **Lightweight**: 외부 의존성 0%, 100% 순수 자바스크립트로 최상의 성능 제공.
* **Extensible**: 정규식 및 함수형 검증을 통해 복잡한 비즈니스 로직도 유연하게 처리.

<br>
<br>

## 💡 Configuration
생성자의 두 번째 인자로 옵션을 설정하여 라이브러리의 동작을 제어할 수 있습니다.
| 옵션 | 설명 | 기본값 |
| --- | --- | --- |
| `required` | 필수 입력 여부 | `false` |
| `type` | 내장 필터 타입(int, email, korean 등) | `null` |
| `regexp` | 필터링용 커스텀 정규식 | `null` |
| `validate.regexp` | 검증용 커스텀 정규식 | `null` |
| `selector` | 부모 요소 내 적용할 타겟 셀렉터 | `input, textarea` |

<br>
<br>

## 💡 Advanced Usage
* **한글 필수 입력 필드**
```javascript
new KokInputFilter("#nameField", { type: "korean", required: true });
nameField.addEventListener('input', e => {
    e.target.classList.remove('success', 'danger');
});
nameField.addEventListener('success', e => {
    e.target.classList.remove('success', 'danger');
    e.target.classList.add('success');
});
nameField.addEventListener('error', e => {
    e.target.classList.remove('success', 'danger');
    e.target.classList.add('danger');
});
```

* **길이 3 이상의 숫자 입력 필드**
```javascript
new KokInputFilter("#customValidate", { 
    validate: { 
        regexp: /^[0-9]{3,}$/
    }
});
customValidate.addEventListener('input', e => {
    e.target.classList.remove('success', 'danger');
});
customValidate.addEventListener('success', e => {
    e.target.classList.remove('success', 'danger');
    e.target.classList.add('success');
});
customValidate.addEventListener('error', e => {
    e.target.classList.remove('success', 'danger');
    e.target.classList.add('danger');
});
```

<br>
<br>

## 📝 License
This project is licensed under the MIT License.
