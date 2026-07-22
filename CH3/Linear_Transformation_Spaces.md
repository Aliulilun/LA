# 線性代數核心筆記：核空間 (Kernel) 與像空間 (Image / Range)

> **學術前提：**
> 假設 \(V\) 與 \(W\) 為定義在同一個純量體（Field）上的向量空間，且
>
> \[
> T:V\rightarrow W
> \]
>
> 是一個線性轉換（Linear Transformation）。

---

# 一、嚴格數學定義與幾何意義

## 1. 核空間（Kernel）

### 代數定義

核空間是 **定義域 \(V\)** 的一個子集，包含所有被映射到對應域零向量的向量：

\[
\ker(T)=\{\,v\in V \mid T(v)=0_W\,\}
\]

---

### 幾何意義

可以把 Kernel 想成：

- 資訊黑洞（Information Black Hole）
- 被壓縮掉的方向（Collapsed Directions）

凡是落在

\[
\ker(T)
\]

中的向量，經過線性轉換後都會變成

\[
0_W
\]

因此：

- 長度消失
- 方向消失
- 無法從輸出恢復原來的資訊

---

### 與矩陣的關係

若

\[
T(x)=Ax
\]

則

\[
\ker(T)=N(A)
\]

其中

\[
N(A)=\{x\mid Ax=0\}
\]

稱為 **Null Space（零空間）**。

---

# 2. 像空間（Image / Range）

### 代數定義

像空間是 **對應域 \(W\)** 的一個子集：

\[
\operatorname{Im}(T)
=
\{\,T(v)\mid v\in V\,\}
\]

---

### 幾何意義

Image 可以理解為：

> 線性轉換真正能夠到達的所有位置。

雖然目標空間是

\[
W
\]

但真正能抵達的只有

\[
\operatorname{Im}(T)\subseteq W
\]

因此 Image 又稱為：

- Reachable Space
- Range

---

### 與矩陣的關係

若

\[
T(x)=Ax
\]

則

\[
\operatorname{Im}(T)=CS(A)
\]

其中

\[
CS(A)
\]

表示 **Column Space（行空間／直行空間）**。

原因是

\[
Ax
=
x_1a_1+x_2a_2+\cdots+x_na_n
\]

也就是所有直行向量的線性組合。

---

# 二、證明 Kernel 與 Image 都是子空間

一個集合若要成為子空間（Subspace），需滿足：

1. 包含零向量
2. 對加法封閉
3. 對純量乘法封閉

---

## 1. Kernel 是子空間

令

\[
u,v\in\ker(T)
\]

則

\[
T(u)=0,\qquad
T(v)=0
\]

任意純量

\[
c
\]

有

\[
\begin{aligned}
T(cu+v)
&=cT(u)+T(v) \\
&=c(0)+0\\
&=0
\end{aligned}
\]

因此

\[
cu+v\in\ker(T)
\]

故 Kernel 對線性組合封閉，因此是子空間。

---

## 2. Image 是子空間

令

\[
w_1,w_2\in\operatorname{Im}(T)
\]

則存在

\[
v_1,v_2\in V
\]

使得

\[
T(v_1)=w_1,\qquad
T(v_2)=w_2
\]

因此

\[
\begin{aligned}
cw_1+w_2
&=cT(v_1)+T(v_2)\\
&=T(cv_1+v_2)
\end{aligned}
\]

因為

\[
cv_1+v_2\in V
\]

故

\[
cw_1+w_2
\]

仍然有前像，因此

\[
cw_1+w_2\in\operatorname{Im}(T)
\]

Image 為子空間。

---

# 三、Rank–Nullity Theorem（秩－零度定理）

若

\[
T:V\rightarrow W
\]

且

\[
V
\]

有限維，則

\[
\boxed{
\dim(\ker(T))
+
\dim(\operatorname{Im}(T))
=
\dim(V)
}
\]

---

## Rank（秩）

\[
\operatorname{Rank}(T)
=
\dim(\operatorname{Im}(T))
\]

表示：

> 有多少維度成功傳遞到了輸出空間。

---

## Nullity（零度）

\[
\operatorname{Nullity}(T)
=
\dim(\ker(T))
\]

表示：

> 有多少維度被壓縮成零。

---

因此

\[
\boxed{
\text{Rank}
+
\text{Nullity}
=
\dim(V)
}
\]

可以理解成：

> **輸入空間的所有維度，不是成功保留下來，就是被壓縮掉。**

---

# 四、利用 Kernel 與 Image 判定映射性質

| 映射性質 | 幾何意義 | 代數判定 | 推導 |
|-----------|----------|----------|------|
| **單射 (Injective)** | 不同輸入得到不同輸出 | \(\ker(T)=\{0\}\) | 若 \(T(x)=T(y)\)，則 \(T(x-y)=0\)。因此 \(x-y\in\ker(T)\)。若 Kernel 只有零向量，則 \(x=y\)。 |
| **滿射 (Surjective)** | 所有目標點皆可抵達 | \(\operatorname{Im}(T)=W\) | Image 等於整個對應域，因此沒有遺漏任何向量。 |
| **雙射 (Bijective)** | 一一對應，可逆 | 同時滿足單射與滿射 | 此時存在唯一反函數 \(T^{-1}\)。 |

---

# 五、總整理

設

\[
T:V\rightarrow W
\]

則：

## Kernel

- 位於 **定義域 \(V\)**
- 是 Null Space
- 描述哪些向量會變成零
- 用來判斷是否 Injective

---

## Image

- 位於 **對應域 \(W\)**
- 是 Column Space
- 描述真正能到達哪些位置
- 用來判斷是否 Surjective

---

## Rank–Nullity

\[
\boxed{
\dim(V)
=
\operatorname{Rank}(T)
+
\operatorname{Nullity}(T)
}
\]

其中

- Rank = 保留下來的維度
- Nullity = 消失的維度

兩者相加一定等於原始空間的維度。
