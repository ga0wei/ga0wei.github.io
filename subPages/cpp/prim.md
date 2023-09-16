

# [🏡Home](/) |   [👨‍💻About](/about)  |   [🗂️Texts](/allTexts)   |   [💬Web Quotes](/webQuotes)

#  📖Prim 算法

✍Author：[GaoWei](/about)  

📆Data：23 / 09 / 16

📆Modified：-- / -- / --

---




## Prim 算法

一直找里目前的图里面最近的节点。

两层循环，时间复杂度O(n^2)



```c++
#include <bits/stdc++.h>

using namespace std;

#define inf INT_MAX

vector<int> prim(vector<vector<int >> &graph, int head) {
    int n = graph.size();
    vector<int> res;

    vector<int> distance(n, inf);
    vector<int> visited(n, 0);

    visited[head] = 1;
    distance[head] = 0;
    int to_add = 0;
    int to_cmp = head;
    int min_dis = inf;

    res.push_back(head);

    //找到权值
    for (int cnt = 1; cnt < n; ++cnt) {
        min_dis = inf;
        for (int i = 0; i < n; ++i) {
            if (!visited[i]) {
                distance[i] = min(distance[i], graph[to_cmp][i]);
                if (min_dis > distance[i]) {
                    min_dis = distance[i];
                    to_add = i;
                }
            }
        }
        res.push_back(to_add);
        visited[to_add] = 1;
        to_cmp = to_add;
        
        //找到权值了，在找对应的边
        cout << "to add point: " << to_add <<'\t';
        for (int i = 0; i < n; ++i) {
            if (visited[i] && graph[to_add][i] == distance[to_add]) {
                cout << "to add edge: " << i<<" -> "<<to_add << endl;
            }
        }
    }
    return res;
}


int main() {
    vector<vector<int >> graph = {
            {inf, 6,   1, 5,   inf, inf},
            {6,   inf, 5, inf, 3,   inf},
            {1,   5, inf, 5,   6,   4},
            {5,   inf, 5, inf, inf, 2},
            {inf, 3,   6, inf, inf, 6},
            {inf, inf, 4, 2,   6,   inf}
    };
    auto res = prim(graph, 3);

    for (auto v: res) {
        cout << v << endl;
    }
}
```