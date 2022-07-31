---
layout: single
title: "Oculus Quest2 Development Setting"
---

## [UnityVR] Oculus Quest2 개발 세팅

Device : Oculus Quest2
Minimum System Requirements :  2.0+ GHz processor, 2GB System RAM
Development Environment : Windows10 / Unity / VisualStudio2019



오큘러스 퀘스트2 개발을 위해서 유니티 에디터 버전은 **최소 2020.3 LTS** 이어야 한다. 다음 유니티 에디터 아카이브를 참조해 버전을 받으면 된다. [(https://unity3d.com/kr/get-unity/download/archive](https://tmdgns1507.github.io/Programmers_GreatestNum/))
Unity Hub에서 (아카이브를 통한) Unity 버전을 설치할 때, 아래 사진과 같이 **Android Build Suppport** 를 체크하고 하위에 **"Android SDK & NDK Tools", "OpenJDK"**를 체크해야한다.
이 설정은 필요한 라이브러리를 빌드하고 최종적으로 출력 패키지(APK)를 생성하는 데 필요한 도구 체인(컴파일러&링커)이 포함되기에 반드시 체크해야 한다.

![img](https://scontent-ssn1-1.xx.fbcdn.net/v/t39.2365-6/92497029_532446234352560_2105251449326796800_n.png?_nc_cat=108&ccb=1-7&_nc_sid=ad8a9d&_nc_ohc=anETaCixrf0AX9-MFhp&_nc_ht=scontent-ssn1-1.xx&oh=00_AT9zs5UjEHfhKMA1896DJLsKsJ_N7huiUQycyZpfsKSGpg&oe=62EB8958)

(참조 : [https://developer.oculus.com/documentation](https://developer.oculus.com/documentation))



그 다음, 프로젝트를 임의로 만들어서 Open한 뒤에, Asset Store에 들어가서 Oculus Integration(Free)를 설치한다. 설치 한 뒤, Unity Editor로 들어와 Package Manager를 통해서 Oculus Intergration을 Import 시켜준다.
Oculus Integration은 Oculus에서 제공하는 디바이스의 입력, 오브젝트 등 개발에 필요한 기본 요소들을 제공해준다.

