---
layout: default
---

<!-- mathjax config similar to math.stackexchange -->
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    TeX: { equationNumbers: { autoNumber: "AMS" }},
    tex2jax: {
      inlineMath: [ ['$','$'] ],
      processEscapes: true
    },
    "HTML-CSS": { matchFontHeight: false },
    displayAlign: "left",
    displayIndent: "2em"
  });
</script>

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jquery-balloon-js@1.1.2/jquery.balloon.min.js" integrity="sha256-ZEYs9VrgAeNuPvs15E39OsyOJaIkXEEt10fzxJ20+2I=" crossorigin="anonymous"></script>
<script type="text/javascript" src="../../../assets/js/copy-button.js"></script>
<link rel="stylesheet" href="../../../assets/css/copy-button.css" />


# :warning: algebra/number/cached_egcd.cpp

<a href="../../../index.html">Back to top page</a>

* category: <a href="../../../index.html#eff53351317ed5e83ba9ff9cfd3cdf3c">algebra/number</a>
* <a href="{{ site.github.repository_url }}/blob/master/algebra/number/cached_egcd.cpp">View this file on GitHub</a>
    - Last commit date: 2019-08-18 11:19:23+09:00




## Code

<a id="unbundled"></a>
{% raw %}
```cpp
#define MOD 1000000007
#define MAX 20000005
long long cache_f[MAX],cache_invf[MAX];
void init_cache_egcd(){
    long long maxn=MAX;
    cache_f[0]=1; for (long long i=1;i<maxn;i++) cache_f[i]=cache_f[i-1]*i%MOD;
    cache_invf[0]=cache_invf[1]=1; for (long long i=2;i<maxn;i++) cache_invf[i]=MOD-(MOD/i)*cache_invf[MOD%i]%MOD;
    for (long long i=2;i<maxn;i++) cache_invf[i]=cache_invf[i-1]*cache_invf[i]%MOD;
}

long long C(long long x,long long y){
    if (y<0||y>x) return 0;
    return cache_f[x]*cache_invf[y]%MOD*cache_invf[x-y]%MOD;
}
long long egcd(long long a){
    return cache_invf[a]*cache_f[a-1]%MOD;
}
```
{% endraw %}

<a id="bundled"></a>
{% raw %}
```cpp
#line 1 "algebra/number/cached_egcd.cpp"
#define MOD 1000000007
#define MAX 20000005
long long cache_f[MAX],cache_invf[MAX];
void init_cache_egcd(){
    long long maxn=MAX;
    cache_f[0]=1; for (long long i=1;i<maxn;i++) cache_f[i]=cache_f[i-1]*i%MOD;
    cache_invf[0]=cache_invf[1]=1; for (long long i=2;i<maxn;i++) cache_invf[i]=MOD-(MOD/i)*cache_invf[MOD%i]%MOD;
    for (long long i=2;i<maxn;i++) cache_invf[i]=cache_invf[i-1]*cache_invf[i]%MOD;
}

long long C(long long x,long long y){
    if (y<0||y>x) return 0;
    return cache_f[x]*cache_invf[y]%MOD*cache_invf[x-y]%MOD;
}
long long egcd(long long a){
    return cache_invf[a]*cache_f[a-1]%MOD;
}

```
{% endraw %}

<a href="../../../index.html">Back to top page</a>
