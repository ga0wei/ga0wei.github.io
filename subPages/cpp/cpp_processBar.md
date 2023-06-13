# [🏡Home](/) |   [👨‍💻About](/about)  |   [🗂️Texts](/allTexts)
# 📖C++ 实现进度条


✍Author：[GaoWei](/about)  

📆Data：23 / 06 / 01

📆Modified：-- / -- / --

---




C++ 实现进度条
```c++
#include <bits/stdc++.h>
#include "windows.h"

void process(int x) {
    char a[4] = {'-', '\\', '|', '/'};
    std::cout << '\r';
    std::cout << '[';
    std::cout << std::string(x / 2, '=');
    if (x / 2 <= 49) {
        std::cout << '>';
    }
    if (x / 2 <= 48) {
        std::cout << a[x % 4];
    }
    if (x / 2 <= 48) {
        std::cout << std::string(48 - x / 2, ' ');
    }
    std::cout << ']';
    std::cout << x << '%';
}

int main() {
    for (int i = 0; i <= 100; i++) {
        process(i);
        Sleep(50);
    }
    std::cout<<std::endl;
    std::cout<<"complete"<<std::endl;
    system("pause");
}
```