---
title: "Přetížitelné operátory (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7487f398ec412c4a302054ade20800f431e2c793
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="overloadable-operators-c-programming-guide"></a>Přetížitelné operátory (Průvodce programováním v C#)

C# umožňuje uživatelem definované typy přetížení operátory definováním statické členské funkce pomocí [operátor](../../../csharp/language-reference/keywords/operator.md) – klíčové slovo. Ne všechny operátory mohou být přetíženy, ale a ostatní uživatelé mají omezení, jak je uvedeno v této tabulce:

| Operátory | Overloadability |
| --------- | --------------- |
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [++](../../../csharp/language-reference/operators/increment-operator.md), [--](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Tyto unární operátory může být přetížený.|
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md), [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [>>](../../../csharp/language-reference/operators/right-shift-operator.md)|Tyto binární operátory může být přetížený.|
|[==](../../../csharp/language-reference/operators/equality-comparison-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|Operátory porovnání mohou být přetíženy (ale viz poznámka pod touto tabulkou).|
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Podmíněné logické operátory nemohou být přetíženy, ale jsou vyhodnocovány pomocí `&` a <code>&#124;</code>, které mohou být přetíženy.|
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|Operátor indexování pole nemohou být přetíženy, ale můžete definovat indexery.|
|[(T)x](../../../csharp/language-reference/operators/invocation-operator.md)|Operátor přetypování nemohou být přetíženy, ale můžete definovat nové operátory převodu (viz [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md)).|
|[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [\*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Operátory přiřazení nemohou být přetíženy, ale `+=`, například vyhodnotí pomocí `+`, které mohou být přetíženy.|
|[=](../../../csharp/language-reference/operators/assignment-operator.md), [. ](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [?? ](../../../csharp/language-reference/operators/null-conditional-operator.md), [ -> ](../../../csharp/language-reference/operators/dereference-operator.md), [ => ](../../../csharp/language-reference/operators/lambda-operator.md), [f(x)](../../../csharp/language-reference/operators/invocation-operator.md), [jako](../../../csharp/language-reference/keywords/as.md), [zaškrtnutí ](../../../csharp/language-reference/keywords/checked.md), [nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md), [výchozí](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), [delegovat](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [je](../../../csharp/language-reference/keywords/is.md), [nové](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Tyto operátory nemohou být přetíženy.|

> [!NOTE]
> Operátory porovnání přetížení, musí být přetíženy v párech; To znamená pokud `==` je přetížena `!=` také musí být přetížený. Platí také nastavena hodnota true, kde přetížení `!=` vyžaduje přetížení pro `==`. Totéž platí pro operátory porovnání `<` a `>` a `<=` a `>=`.

Přetížení operátor na vlastní třídu vyžaduje vytvoření metody pro třídu se správným podpisem. Metodu, musí mít název "operátor X" kde X je název nebo symbol operátoru přetížen. Unární operátory mít jeden parametr a binární operátory mít dva parametry. Jeden parametr v každém případě musí být stejného typu, třídu nebo strukturu, který deklaruje operátor.

```csharp
public static Complex operator +(Complex c1, Complex c2)
{
    return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
}
```

Je běžné tak, aby měl definice, které jednoduše vrátit okamžitě s výsledkem výrazu.  Je syntaxe zástupce pomocí `=>` v takových situacích.

```csharp
public static Complex operator +(Complex c1, Complex c2) =>
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
  
// Override ToString() to display a complex number in the traditional format:
public override string ToString() => $"{this.real} + {this.imaginary}";
```

Další informace najdete v tématu [postupy: použití přetížení operátoru pro vytvoření třídy reprezentující komplexní čísla](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).

## <a name="see-also"></a>Viz také

[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Příkazy, výrazy a operátory](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
[Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
[Proč se přetížené operátory vždy v C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
