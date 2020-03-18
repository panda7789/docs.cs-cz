---
title: throw - C# Reference
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399334"
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)

Signalizuje výskyt výjimky během provádění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e];
```

kde `e` je instancí třídy <xref:System.Exception?displayProperty=nameWithType>odvozené z . Následující příklad používá `throw` příkaz k <xref:System.IndexOutOfRangeException> vyvolání, pokud argument `GetNumber` předaný metodě s názvem neodpovídá platnému indexu vnitřního pole.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Metoda volající pak `try-catch` použít `try-catch-finally` nebo blok pro zpracování vyvolána výjimku. Následující příklad zpracovává výjimku vyváděnou `GetNumber` metodou.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Opětovné vyvolání výjimky

`throw`lze také použít `catch` v bloku znovu vyvolat výjimku `catch` zpracovány v bloku.  V tomto `throw` případě nebere výjimku operand. Je nejužitečnější, když metoda předá argument z volajícího na jinou metodu knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu. Například následující příklad znovu vyvolá, <xref:System.NullReferenceException> který je vyvolán při pokusu o načtení prvního znaku neinicializovaného řetězce.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> `throw e` Syntaxi v `catch` bloku můžete také použít k vytvoření instance nové výjimky, kterou předáte volajícímu. V tomto případě trasování zásobníku původní výjimku, <xref:System.Exception.StackTrace> která je k dispozici z vlastnosti, není zachována.

## <a name="the-throw-expression"></a>Výraz `throw`

Počínaje C# 7.0, `throw` lze použít jako výraz, stejně jako příkaz. To umožňuje výjimku vyvolat v kontextech, které byly dříve nepodporované. Mezi ně patří:

- [podmíněný operátor](../operators/conditional-operator.md). Následující příklad používá `throw` výraz k <xref:System.ArgumentException> vyvolání metody, pokud je metoda předána prázdnému řetězci. Před C# 7.0, tato logika `if` / `else` by se musel zobrazit v příkazu.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [operátor null-coalescing](../operators/null-coalescing-operator.md). V následujícím příkladu `throw` se výraz používá s operátorem null-coalescing k vyvolání `null`výjimky, pokud je řetězec přiřazený vlastnosti `Name` .

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- výraz-tělesně [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metoda. Následující příklad ilustruje metodu s výrazem, <xref:System.InvalidCastException> která vyvolá, <xref:System.DateTime> protože převod na hodnotu není podporován.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [C# Klíčová slova](index.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
