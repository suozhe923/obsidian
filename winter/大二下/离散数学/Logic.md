***Proposition(命题)***: a declarative(声明性) sentence that is either true or false (not both)
- Declarative sentence: a sentence that makes a statement, while it does not ask a question or give an order  
- Either true or false: fixed(固定); _no variable_ involved
**Truth value** of a proposition:
- true, denoted by T 
- false, denoted by F.
**Propositional variables**: variables that represent propositions(like p,q,r,s...)
__Compound Propositions(复合命题)__:
- Negation $\lnot$ 
	$\lnot$p is read "not p"
- Conjunction(And) $\land$
	p$\land$q is "p and q"
- Disjunction(Or) $\lor$
- Exclusive or $\oplus$
- Implication $\to$
	p $\to$ q is 
	- if p, then q
	- p implies q
	- p is sufficient for q
	- q is necessary for p
	- q follows from p
	- p only if q
	The converse(逆命题) of p → q is q → p.
	The contrapositive(逆否) of p → q is ¬q → ¬p.
		逆否命题有着相同的 truth value
	The inverse(否) of p → q is ¬p → ¬q.
- Biconditional $\leftrightarrow$
	- p if and only if q
	- p is necessary and sufficient for q
	- if p then q, and conversely
	- p iff q


__Tautology and Contradiction__
- Tautology(恒真式,重言式): A compound proposition that is __always true__, no matter what the truth values of the propositional variables that occur in it.
- Contradiction: A compound proposition that is __always false__
- Contingency: A compound proposition that is __neither__ a tautology nor a contradiction.
__Logical Equivalances:__
- The compound propositions p and q are called logically equivalent, denoted by(记作) p $\equiv$ q or p $\Leftrightarrow$ q, if p $\leftrightarrow$ q is a tautology
- two compound propositions are equivalent if they always have the same truth value.

- De Morgan's Laws:	
$$
\begin{aligned}
\lnot(p\lor q) \equiv \lnot p \land \lnot q \\
\lnot(p\land q) \equiv \lnot p \lor \lnot q
\end{aligned}$$
- Identity laws:
$$
\begin{aligned}
p \land T \equiv p \\
q \lor F \equiv p
\end{aligned} $$
- Domination laws:
$$
\begin{aligned}
p \lor T = T \\
p \land F = F
\end{aligned}
$$
- Idempotent laws:
$$
\begin{aligned}
p \lor p = p \\
p \land p = p
\end{aligned}
$$
- Double negation laws:
$$
\begin{aligned}
\lnot(\lnot p) \equiv p
\end{aligned}
$$
- Commutative laws:
$$
\begin{aligned}
p \lor q \equiv q \lor p \\
p \land q \equiv q \land p
\end{aligned}
$$
- Associative laws:
$$
\begin{aligned}
(p \lor q) \lor r \equiv p \lor (q \lor r) \\
(p \land q) \land r \equiv p \land (q \land r) 
\end{aligned}
$$
- Distributive laws:
$$
\begin{aligned}
p \lor (q \land r) \equiv (p \lor q) \land (p \lor r)\\
p\land(q \lor r) \equiv (p \land q) \lor (p \land r)
\end{aligned}
$$
- Others
	- Absorption laws
$$

$$
	- Negation laws
$$
\begin{aligned}
p \lor \lnot p \equiv T \\
p \land \lnot p \equiv F
\end{aligned}
$$
	- Useful law
$$
\begin{aligned}
p \to q \equiv \lnot p \lor q
\end{aligned}
$$
E1: __Show that $(p \land q) \to  p$ is a tautology__
proof:
$$
\begin{align}
(p \land q ) \to p &\equiv \lnot (p \land q) \lor p \qquad --Useful\ law\\
&\equiv (\lnot p \lor \lnot q) \lor p \qquad -- De \ Morgan's\ laws \\
&\equiv (\lnot q \lor \lnot p) \lor p \qquad --Commutative law\\
&\equiv \lnot p \lor (\lnot q \lor q) \qquad -- Associative\ laws \\
&\equiv \lnot p \lor T \qquad -- Negation\ laws \\
&\equiv T \qquad --Domination\ laws 
\end{align}
$$

E2:__Show that $p \to q \equiv \lnot q \to \lnot p$__
$$
\begin{aligned}
Proof: \lnot q \to \lnot p &\equiv \lnot(\lnot q) \lor (\lnot p) \qquad Useful\\
&\equiv q \lor (\lnot p) \qquad Double negation\\
&\equiv (\lnot p) \lor q \qquad Communtative\\
&\equiv p \lor q \qquad Useful
\end{aligned}
$$

Predicate Logic
	_make statements with **variables**_
	- A propositional function P(x) assigns a value T or F to each x depending on whether the property holds or not for x
		- E: P(x) denote(表示) the statement "x > 3"
		- P(2) is F, P(4) is T
		- P(x) is not a proposition but P(2) is
	- A __predicate__ is a statement P($x_1,x_2,..x_n$) that contains n variables $x_1,x_2,..x_n$. It becomes a proposition when specific values are substituted for the variables $x_1, x_2, ... x_n$
	- the __domain(universe)__ D of the predicate variables $x_1, x_2, ... x_n$ is the set of all values that may be substituted in place of the variables
	- The __truth set__ of P($x_1,x_2,..x_n$) is the set of all values of the predicate variables ($x_1,x_2,...x_n$) such that the proposition P($x_1,x_2,..x_n$) is true

> Predicate logic permits quantified(量化) statement where variables are substituted for statements about the group of objects.(谓词逻辑允许量化变量为量化语句代替有关对象组的语句。)

Propositional function P(x) -(for all/some x in domain)-> Proposition

Quantified Statements
- Type
	- Universal quantifier $\forall$xP(x)
		- for all xP(x)
		- for every xP(x)
	- Existential quantifier $\exists$xP(x)

Precedence(优先级) of Proposition and Quantifiers

|          Operator          | Precedence |
| :------------------------: | :--------: |
|          $\lnot$           |     1      |
|     $\land$<br>$\lor$      |   2<br>3   |
| $\to$<br>$\leftrightarrow$ |   4<br>5   |
The quantifiers $\forall$ and $\exists$ have higher precedence than all the logical
operators.

$\lnot (\exists xP(x) ) \equiv \forall x (\lnot P(x))$

Nested Quantifiers(嵌套量词)
	==More than one quantifier== may be necessary to capture the meaning of a statement in the predicate logic
 - The order of nested quantifiers __matters__ if quantifiers are of __different__ type.
	E: $\forall x \exists y P(x,y) \ is\ not\ equivalent\ to \ \exists y \forall x P(x,y)$
- The order of nested quantifiers does no matter if quantifiers are of the __same__ type	
$$
\begin{aligned}
\exists x \exists y P(x,y) \equiv \exists y \exists x P(x,y) \\
\forall x \forall y P(x,y) \equiv \forall y \forall x P(x,y)
\end{aligned}
$$
__Argument__
> A sequence of propositions that end with a conclusion
- Premises:
	“If you have a current password, then you can log onto the network.”
	“You have a current password.”
- Therefore,Conclusion:
	“You can log onto the network.”
>An argument is _valid_ if the truth of all its premises implies that the conclusion is true(可以通过前提推导结论)

__Rules of Inference for Propositional Logic__
- modus ponens(law of detachment) 肯定前件式
$$
\begin{aligned}
p \to q \\
p \qquad \\
\rule{1.5cm}{0.4pt}\\
\therefore q \qquad
\end{aligned}
$$
- modus tollens 否定后件式
$$
\begin{aligned}
p \to q \\
\lnot q \qquad \\
\rule{1.5cm}{0.4pt}\\
\therefore \lnot p \qquad
\end{aligned}
$$
- hypothetical syllogism 假言三段论
$$
\begin{aligned}
p \to q \\
\ q \to r \\
\rule{1.5cm}{0.4pt}\\
\therefore p \to r
\end{aligned}
$$
- disjunctive syllogism 选言三段论
$$
\begin{aligned}
p \lor q \\
\lnot p \quad \\
\rule{1.5cm}{0.4pt}\\
\therefore q \quad
\end{aligned}
$$
- Addition
$$
\begin{aligned}
p \qquad\\ \rule{1.2cm}{0.4pt}
\\ \therefore p \lor q
\end{aligned}
$$
- Simplication
$$
\begin{aligned}
p \land q \\
\rule{1.2cm}{0.4pt}\\
\therefore q
\end{aligned}
$$
- Conjunction
$$
\begin{aligned}
p \qquad\\
q \qquad\\
\rule{1.5cm}{0.4pt}\\
\therefore p \land q
\end{aligned}
$$
- Resolution
$$
\begin{aligned}
\lnot p \lor r \\
p \lor q \\
\rule{1.2cm}{0.4pt}\\
\therefore q \lor r
\end{aligned}
$$