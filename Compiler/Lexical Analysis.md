- token(language): a set of strings, e.g., if, identifier, relop
- pattern(grammar): a **rule** defining a token, e.g., if: if; identifier: letter followed by letters and digits; relop: 
- lexeme(sentence): a string matched by the pattern of a token 
![[Pasted image 20241208174052.png]]
- RE alphabet: $a \cup {\epsilon} \cup \{|, \cdot, *, (, ), +, ...\}$
- RE 包含被定義語言的字母集、空字串、運算符號(上面提到的那些) 
![[Pasted image 20241208174056.png]]
![[Pasted image 20241208174101.png]]
- 通常前面 256 給保留字使用，使用者自定義的從 257 開始
- union (*char *id_string; float number-value;) yylval; <= 對 flex 而言，是外部變數
![[Pasted image 20241208174108.png]]
- 定義 ID 時，看到 ws 才會停止，而在看到 ws 之前，任何時候停止應都符合 ID 的定義，因此會選最長的
- 如果同時符合多個 pattern，會選在 list 上看到的第一個
    - if: 同時符合 IF, ID，這時候 IF 放在前面，就會被視為 IF
    - **特例應該放在通例前面**，否則如上面那個例子，關鍵字可能會被視為 ID 而錯亂
- 常出現的 pattern 放在前面