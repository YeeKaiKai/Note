### Intermediate code

- Using **intermediate code** can effectively reduces the required number of compilers
![[Pasted image 20241208173719.png]]
*Figure 1: need 9 compliers*
![[Pasted image 20241208173816.png]]
- *Figure 2: need 3 compliers, each front-end of language can be freely combined with the back-end of the target language*
![[Pasted image 20241208173823.png]]
- Figure 3: usually, the most difficult part is the **target independent optimizer**. 

### Compiler vs Interpreter

- The biggest difference is that **a compiler generates target code, whereas an interpreter does not. Instead, it directly produces output**
- *Figure 4*
![[Pasted image 20241208173831.png]]
### Language

#### What is Language?
- a set of strings on the alphabet
    -  {00, 01, 10, 11}: the set of strings of length 2

#### Operations on Strings

- Figure 5
![[Pasted image 20241208173842.png]]
- Ɛ: the empty string

#### Operations on Languages

- Figure 6
![[Pasted image 20241208173853.png]]
- **Kleene closure**: contains the empty string
- **Positive closure**: doesn't contain the empty string

#### Metalanguage

- Figure 7
![[Pasted image 20241208173900.png]]
- **Metalanguage**: a language used to define another language
- automation can be seen as a compiler
- compile-generator will generate compiler(automation) automatically
![[Pasted image 20241208173909.png]]

#### Definition of Programming Language

![[Pasted image 20241208173919.png]]
- \[element\] : \[metalanguage\]
![[Pasted image 20241208173926.png]]
- \[metalanguage\] : \[automation\], \[analyzer\]