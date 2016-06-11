#include<algorithm>
#include<iostream>
#include<stdio.h>
#include<tuple>
#include<vector>
int main () {
    std::vector <std::tuple<double, long long int, long long int>> lol;
    long long int n, m;
    std::cin >> n >> m;
    double find = 0;
    long long int count = 0;
    for (long long int i = 0; i < n; ++i) {
        long long int a, b;
        std::cin >> a >> b;
        if (b == 0) {
            find += a;
            count++;
        } else {
            std::tuple<double, long long int, long long int> hell;
            double c = (a + 0.0)/b;
            hell = std::make_tuple(c, b, a);
            lol.push_back(hell);
        }
    }
    sort(lol.rbegin(), lol.rend());
    long long int i = 0;
    n = n - count;
    while ((m > 0) && (i < n)) {
        if (m >= std::get<1>(lol[i])) {
            find += std::get<2>(lol[i]);
            m -= std::get<1>(lol[i]);
        } else {
            find += (std::get<0>(lol[i]) * m);
            m = 0;
        }
        i++;
    }
    printf("%.6lf", find);
    return 0;
}
