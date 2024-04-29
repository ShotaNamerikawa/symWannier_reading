# symWannier_reading
空間群に対し特定の変換性を持つ局在ワニエ関数を作るためのsymmetry-adapted Wannier functionの方法について解説する。
間違いが含まれている可能性があるので注意。
# まとめ
- SMWFは空間群の元のうち、あるサイトを変化させない群を集めたとき、その元の作用に対し、中心を固定したまま互いに移り変わるワニエ関数の集まりとして定義される。
- SMWFを構成するためには、SMWFに対応するワニエゲージのブロッホ関数とハミルトニアンゲージのブロッホ関数の変換行列に拘束条件がかかる。
- 上の拘束条件を満たす変換行列が$`U'(\vec{k})=\frac{1}{N_{g_\vec{k}}}{\sum_{g_\vec{k}}...}`$のようなkの小群の平均操作によって求められる。
# 参考文献
1. R.Sakuma PRB 87, 235109 (2013)
2. T.Koretsune CPC 285, 108645 (2022)
3. R.A. Evarestov and V. P. Smirnov, Site Symmetry in Crystals: TheoryandApplications, 2nded.,SpringerSeries inSolidStateSciences (Springer-Verlag,NewYork, 1997).
# 目的と構成
symWannierでやっていることを理解する。特にSymmetry-adapted Wannier Function (SMWF)の構成方法に重点を置いて説明したい。
構成は以下のようにする。
- Symmetry-adapted Wannier Function (SMWF)の定義と空間群に関する対称性
- SMWFの変換性とそれに基づくゲージ変換(U(k))に関する拘束条件
- SMWFを構成できると何が良いのか。
  
記号は基本的にRef.1で用いられているものをそのまま用いる。
# 空間群に対する変換性に基づくSymmetry-adapted Wannier functionの定義
(以下の記述はRef.1の2.A.1を要約したものである。)
空間群を作用させたときに特定の変換性に従うWannier関数をSMWFと定義する。具体的にはあるサイト$`\vec{q}`$に中心をもつWannier関数にそのサイトの固定部分群$`G_\vec{q}`$
(site-symmetry groupともよぶ。空間群の元のうちサイトを変化させない元からなる部分群)の元$`\hat{g}_\vec{q}`$を作用させる。そのときに以下のように変換するワニエ関数をSMWFと呼ぶ。
```math
\hat{g}_\vec{q} W^{(\beta)}_{j1}(\vec{r}) = \sum_{i'=1}^{n_\beta}{d^{(\beta)}_{i'i} (R_q)W^{(\beta)}_{i'1}(\vec{r})}
```
ここで、$`d^{(\beta)}`$は$`\hat{g}`$の回転変換の部分の表現行列である。(Ref.1 では既約表現に従う必要があることを主張している。)
この式は次のように解釈できる。site-symmetry groupの作用に対し、SMWFはそのワニエ中心を固定したままその向きだけが回転の表現に従って変化し、それが同じ中心を持つワニエ関数で展開できる。
群論的に解釈すると、SMWFはSite-symmetry groupの既約表現空間をはる基底である。

上のSMWFから別のサイトにあるワニエ関数を作ることもできる。具体的には空間群を
```math
\hat{g}_{j0} W^{(\beta)}_{j1}(\vec{r}) = 
```
のようになる。ただし、$`\hat{g}_{jn}`$は固定部分群$`G_\vec{q}`$による空間群$`G`$の剰余類の代表元とする。すなわち、
```math
G = \sum_{jn}{\hat{g}_{jn} G_q}
```
#  SMWFの変換性とそれに基づくゲージ変換(U(k))に関する拘束条件
SMWFの変換性を満たすためにはMLWFを構成する際のブロッホ関数の変換(U(k))に拘束条件がかかることを見る。U(k)の拘束条件は
1. 既約k点におけるU(k)とそこから回転で移るfullのk点におけるU(k)の関係
2. 既約k点におけるU(k)が満たすべき条件
   
の2通りがあり、空間群のすべての変換に成り立つ1がより一般的であり、2は変換のうちkを変えない操作(kの小群の元)になり立つ特殊な式である。1の関係からU(k)はIrreducible Brillouin Zone(IBZ)内のkにおける値を決定すると全BZにおける値が自動的に決まることがわかる。これは計算量の軽減につながる。

以下にSMWFの変換性に対応するU(k)の拘束条件(変換性)を導出する。
注意すべきなのはref1では既約なk点におけるハミルトニアンゲージのブロッホ関数が対称操作によって別のk点のブロッホ関数に変換された際にそのk点のブロッホ関数で展開を行うのに対し、
Ref.2では展開せずにそのまま使うのでU(k)の基底が異なることである。これによりU(k)の拘束条件の1の中でRef.1ではブロッホ関数の変換行列が現れるのに際し、Ref.2では現れないという違いが現れる。
(おそらく、この変換したブロッホ関数の取り扱いの違いがentangleバンドでのprojectionにおいてRef.1ではMLWFのoriginalの方法とは異なる手法(Z(k)をkの星まで考えて計算する)を用いるのに対し、Ref.2ではoriginalの方法をそのまま用いることができるという違いにつながる。)
## Ref.1の導出
ワニエゲージすなわちSMWFのバンドを混ぜない単純なフーリエ変換から得られるブロッホ関数の空間群に対する変換性とハミルトニアンの固有状態であるハミルトニアンゲージのブロッホ関数の空間群の変換性を考え、２つのゲージのブロッホ関数の対応関係を考えることでブロッホ関数間のゲージ変換U(k)に対する拘束条件が導出される。

## Ref..2の導出


## Ref.1 Ref.2の違い
# SMWFを構成できると何が良いのか
少なくとも以下のメリットが考えられる。

1. ワニエ軌道の物理的な解釈が行いやすくなる。
2. 既約k点におけるブロッホ基底で表示したテンソル量(グリーン関数 etc ...)をfullのk点に変換する行列を簡単に計算できるようになる。

1に関してはワニエの中心$`\vec{q}`$と"向き"の変換性$`d^{(\beta)}_{i'i} (R_q)`$を適当に定めることでワニエ軌道を原子軌道や分子軌道ライクに変換させられることからいえる。
2に関してはワニエの空間群に対する変換性がわかっているとそれをフーリエ変換したブロッホ関数の変換性もわかり、物理量をブロッホ基底で表示したときの変換性も定まることからいえる。
(逆にワニエの変換性がわかっていないとinterpolateしたk点におけるブロッホ関数の変換性がわからない。)
# 疑問点
## ブロッホ関数を空間群によって変換したときの展開性に関する疑問
~Ref.2では既約k点におけるブロッホ関数を空間群の操作$\hat{g}$で対象変換して得られる~
```math
\hat{g} \psi_{\vec{k_i}}(\vec{r})
```
~が移動した先のk点($\vec{k_f} = R_{\hat{g}}\vec{k_i}$)のエネルギーウィンドウ中にある部分空間のブロッホ関数で展開できると暗に仮定している気がするが、これは一般には正しくないのではないか？
例えば、既約表現に対応するバンドの分散が大きく、既約k点では(アウター)エネルギーウィンドウに入っているが、fullのk点では外に出ているような場合では変換した先のk点ではブロッホ関数を展開できない気がする。(もしかしたらfullのk点ではエネルギーウィンドウを考えず、そのk点のDFTバンド全体で展開すると考えているので問題ないのかもしれない。)~
(2024/3/14、追記)
ハミルトニアンゲージのブロッホ関数であれば$`\hat{g} \psi_{\vec{k_i}}(\vec{r})`$は同じエネルギー固有値を持つはずでありエネルギーウィンドウの中に入るので必ず展開できる。
## ワニエの表現の自由度に関する疑問
Ref.1ではワニエの変換性は自由に選べず、エネルギーウィンドウ内のブロッホ関数の従う表現に対応するものしか取れないと考えているが、Ref.2では必ずprojectionとおなじ変換性をもつワニエ関数を
構成できると考えているように思われる。

Ref.1で述べられているがワニエ関数の変換性はそれを構成するエネルギーウィンドウ内のDFTで計算したk点のブロッホ関数の(既約)表現によって決まるはずであり、任意の表現に従うワニエは構成できないと考えられる。例えばあるkの星の表現に対応するワニエ関数を構成しようとしたときに、その表現に対応するバンドがkの星に属さない別のk点ではエネルギーウィンドウの外にあり、そのバンドに対応するブロッホ関数がワニエを構成するブロッホ関数から除外されている場合が考えられるという状況が考えられる。
ワニエ関数はBZ全体のk点におけるブロッホ関数から構成されるので、このような場合は表現に従うワニエ関数は得られないと予想される。

したがって、Ref.2の方法のようにinitial projection(原子軌道)の変換性と同じような変換性を持つワニエを構成できるかどうかは自明ではない気がする。
もしエネルギーウィンドウ内にそのように変換するワニエに対応するブロッホ関数がない、あるいはあるk点では含まれるが別のk点では含まれない場合はどうなるのか？
(あるいは無理やり従うように拘束条件をかけているのか？常にそのようなことができるのか？)
