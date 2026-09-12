<!-- 2026-08-08 18:11 KST 작성 -->

# 손글씨 숫자 인식 (3장 실습)

마우스로 그린 숫자를 인식하는 앱이다. 같은 프로그램을 데스크톱 앱과 웹 앱 두 버전으로 만들어 나란히 두었다.

실행 방법 안내

- **데스크톱** — `cd desktop_version && python3 app.py` (윈도우는 `py app.py`)
- **웹** — `cd web_version && python3 -m http.server 8000` 을 실행한 뒤 http://localhost:8000 접속
- **배포본** — https://logistex.github.io/Study01_MNIST_mac/

학습된 가중치(`desktop_version/mnist_cnn.pt`)가 들어 있으므로 **학습 없이 바로 실행된다.**

## 필요한 것

| 구분 | 설치 |
|---|---|
| 데스크톱 앱 실행 | `pip install torch pillow` |
| 다시 학습까지 | `pip install torch torchvision` (`pillow` 가 함께 깔린다) |
| 웹 앱 실행 | **없다.** 외부 라이브러리를 쓰지 않는다 |

`tkinter` 는 파이썬에 함께 들어 있다. `torch`를 설치한다고 `pillow`가 함께 설치되지는 않으므로 데스크톱 앱만 실행할 때도 `pillow` 를 따로 깔아야 한다.

## 다시 학습하기

`cd desktop_version && python3 train.py` 를 실행한다. **5 에포크에 1분 안팎 걸린다**(M2 맥북 에어 실측: GPU 50초, CPU 1분 30초). 에포크(epoch)는 학습 데이터 6만 장 전체를 한 번 훑는 단위이고, 5 에포크는 같은 데이터를 5번 반복해서 학습한다는 뜻이다. MNIST 원본은 용량 때문에 저장소에 없고, `train.py` 를 처음 실행할 때 자동으로 내려받는다. 이때 `CERTIFICATE_VERIFY_FAILED` 같은 SSL 오류가 나면 [desktop_version/CLAUDE.md](desktop_version/CLAUDE.md) 의 「환경 제약」 절에 있는 직접 내려받기 명령을 쓴다.

자세한 내용은 [CLAUDE.md](CLAUDE.md) 를 참고한다.
