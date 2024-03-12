# symWannier_reading
# Ref 
1. R.Sakuma PRB 87, 235109 (2013)
2. T.Koretsune CPC 285, 108645 (2022)
# Purpose and composition
symWannierでやっていることを理解する。特にSymmetry-adapted Wannier Function (SMWF)の構成方法に重点を置いて説明したい。
構成は以下のようにする。
- Symmetry-adapted Wannier Function (SMWF)の定義と空間群に関する対称性
- SMWFの変換性とそれに基づくゲージ変換(U(k))に関する拘束条件
- SMWFを構成できると何が良いのか。
  
記号は基本的にref1で用いられているものをそのまま用いる。
# Symmetry-adapted Wannier functionの定義と空間群に関する対称性
空間群(磁気空間群はとりあえず考えない)を作用させたときに特定の変換性に従うWannier関数をSMWFと定義する。これはref.1によると
あるサイト$\vec{q}$に中心をもつWannier関数にそのサイトの固定部分群$G_\vec{q}$(site-symmetryともよぶ。空間群の元のうちサイトを変化させない元からなる部分群)の元を作用させたときに
以下のように変換する関数である。
```math
\hat{g}_\vec{q} W^{(\beta)}_{j1}(\vec{r}) = \sum_{i'=1}^{n_\beta}{d^{(\beta)}_{i'i} (R_q)W^{(\beta)}_{i'1}(\vec{r})}
```
ここで、$d^{(\beta)}$は回転部分に対する変換の表現行列である。
これは中心を変化させない空間群の作用に対し、SMWFはそのワニエ中心を固定したままその向きだけが回転の表現に従って変化すると解釈できる。

上ではsite-symmetryに対する変換性を定義したがこれによってサイトを変えるような一般の空間群に対する変換性も定まる。その変換性は

のようになる。
#  SMWFの変換性とそれに基づくゲージ変換(U(k))に関する拘束条件
SMWFの変換性を満たすためにはMLWFを構成する際のブロッホ関数の変換(U(k))に拘束条件がかかることを見る。U(k)の拘束条件は
1. 既約k点におけるU(k)とそこから回転で移るfullのk点におけるU(k)の関係
2. 既約k点におけるU(k)が満たすべき条件
   
の2通りがあり、空間群の変換に関する同じ式に対し、1はkを変える操作、2はkを変えない操作(kの小群の元)を考えることによって導出できる。また、1の関係からU(k)はIrreducible Brillouin Zone(IBZ)における値を決定すると全BZにおける値が自動的に決まることがわかる。


SMWFの変換性に対応するU(k)の変換性を導出する。ref1,2で導出方法が異なり、拘束条件1に対し異なる結果が出るのでそれぞれの導出を追う。(違いに関しては次のセクションで考える。)

## ref.1の導出
SMWFに対するワニエゲージ、すなわちバンドを混ぜずにフーリエ変換を行ったブロッホ関数の空間群に対する変換性とハミルトニアンゲージのブロッホ関数の空間群の変換性を考え、
２つのゲージのブロッホ関数の対応関係を考えることでブロッホ関数間のゲージ変換U(k)に対する拘束条件が導出される。

## ref.2の導出


ゲージ(U(k))の変換性が異なる。

# 疑問点
ref2では既約k点におけるブロッホ関数を空間群の操作$\hat{g}$で対象変換して得られる
```math
\hat{g} \psi_{\vec{k_i}}(\vec{r})
```
が移動した先のk点($\vec{k_f} = R_{\hat{g}}\vec{k_i}$)のエネルギーウィンドウ中にある部分空間のブロッホ関数で展開できると暗に仮定している気がするが、これは一般には正しくないのではないか？
例えば、既約表現に対応するバンドの分散が大きく、既約k点では(アウター)エネルギーウィンドウに入っているが、fullのk点では外に出ているような場合では変換した先のk点ではブロッホ関数を展開できない気がする。(もしかしたらfullのk点ではエネルギーウィンドウを考えず、そのk点のDFTバンド全体で展開すると考えているので問題ないのかもしれない。)
