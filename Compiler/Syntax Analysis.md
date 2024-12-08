

![[Pasted image 20241208174224.png]]
- 方法相同(leftmost)，但在 production 上選擇不同，產生了兩種語法樹 => ambiguous grammar
![[Pasted image 20241208174229.png]]
- CFG 包含了 RE
- 雖然 CFG 都可以做到，但語彙分析不需要用到 CFG 那麼多的功能
![[Pasted image 20241208174235.png]]
- S = {$\varepsilon$, ab, aabb, aaabbb, ...} = {$a^ib^i \vert i \ge 0$}
- Stack 可以用來確認兩個輸入的數量是不是一樣的
- L = {$wcw^{-1} \vert w$ in $(a \vert b)^*$}
 => S -> aSa 
\.\.\.\.\.\.\.\.\.\.\.| bSb
\.\.\.\.\.\.\.\.\.\.\.| c
![[Pasted image 20241208174247.png]]
- 理論上會先推 A，論結論來說會 backtrack，所以步驟上忽略
- 一個一個 terminal 看，可以推論就推，沒辦法就放入 stack
- buttom-up 是做 reduction，不是推導，只是用推導的方式觀察的話，其實是用 rightmost 的方式做推導
![[Pasted image 20241208174253.png]]
- Parsing driver + Parsing table = finite automata
    - Shift/Reduce Conflict: 已經符合一種 reduction 的情況下，shift 後有可能符合另一個 reduction
    - Reduce/Reduce Conflict: 同時有兩種條件符合 reduction
![[Pasted image 20241208174300.png]]
![[Pasted image 20241208174307.png]]
- 會同時將 reduce 後的 nonterminal/terminal 以及新的狀態 push 上去 stack
![[Pasted image 20241208174312.png]]
- sn: 做 shift，將狀態轉換到 n
- rn: 做 reduce，用第 n 個 production，並看 pop 掉後、push 新的 nonterminal 之前是什麼狀態，用那個狀態查 Goto table 來決定新的狀態
![[Pasted image 20241208174318.png]]
- Example
    - step 1: 狀態 0，看到 id，做 s5 (push id, push state 5)
    - step 2: 狀態 5，看到 +，做 r6 (reduce by production 6)，pop 後狀態為 0，nonterminal 為 F，查 Goto table 得知 push F 後 push state 3
    - ...
![[Pasted image 20241208174325.png]]
![[Pasted image 20241208174331.png]]
- 1: 每個 symbol 都會附帶一個 state，因此是 pop 掉 2 * symbol個數 的數量
![[Pasted image 20241208174337.png]]
- 由下而上算
- 如果推到最後會空掉，則空字串也會成為 first sets 之一
![[Pasted image 20241208174343.png]]
- $X \rightarrow Y_1 Y_2 ... Y_k$
    - 如果 $Y_1$ 不可能為空字串，則 $Y_2$ 的 first sets 不可能為 X 的 first sets，反之則有可能，$Y_3 ...$ 也是以此類推。如果 $Y_1$ 到 $Y_k$ 都有空字串，則 X 的 first sets 會包含空字串。
![[Pasted image 20241208174350.png]]
- First(F) = First((E)) $\cup$ First(id) = { ( } $\cup$ { id } = { (, id }
- First(T') = First(*FT') $\cup$ First($\epsilon$) = {\*} $\cup$ {$\epsilon$} = { \*, $\epsilon$ }
- First(T) = First(FT') = { (, id }
- First(E') = First(+TE') $\cup$ First($\epsilon$) = {+} $\cup$ {$\epsilon$} = { +, $\epsilon$ }
- First(E) = First(TE') = { (, id }
![[Pasted image 20241208174357.png]]
- 反正很複雜規則要看清楚
![[Pasted image 20241208174403.png]]
- Follow sets 由上而下算
![[Pasted image 20241208174410.png]]
- $\cdot$ 代表前面的 token 已經分析完了，接著要分析後面的 token
![[Pasted image 20241208174416.png]]
- NPDA->NPDA（同一狀態，右邊是內部狀態），全部會同時走，只要有一個符合就 OK
![[Pasted image 20241208174421.png]]
- 分析完 production 後做 reduction 的示意圖（把符合的 handle pop 掉後查 GOTO 表把結果 push 上去的那個步驟）
![[Pasted image 20241208174427.png]]
- 加上一個新的 first state E'，他直接指到新的 first state，原因是這樣容易判斷是否是 final state，而不是正在做過程中的轉換
![[Pasted image 20241208174438.png]]
- 紅筆是因為他繼續分析 E，因此會指向 E->... 的狀態（包含他自己）
![[Pasted image 20241208174445.png]]
- 整個 { ... } 視為一個 DFDA
![[Pasted image 20241208174450.png]]
![[Pasted image 20241208174454.png]]
- LR(1) 
    - 當 input symbol 是 a 的時候才做 reduce
    - closure function 需要看 First($\beta$a) 確保 $\beta$ 空掉的情況
    - LR(1) 可以處理的文法比 SLR(1) 還多
![[Pasted image 20241208174507.png]]
- LALR(1)
    - 在 core 相同的情況下做聯集合併

- LALR(k) v.s. LR(k)
    - While LR(k) -> LALR(k), it may produce a new reduce-reduce conflict, but won't produce a new shift-reduce conflict, meaning that LR(k) contains/doesn't contain a shift-reduce conflict if and only if LALR(k) contains/doesn't contain a shift-reduce conflict.