---
description: throw – reference jazyka C#
title: throw – reference jazyka C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142034"
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)

Signalizuje výskyt výjimky během provádění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e];
```

kde `e` je instance třídy odvozené z <xref:System.Exception?displayProperty=nameWithType> . Následující příklad používá `throw` příkaz k vyvolání příkazu, <xref:System.IndexOutOfRangeException> Pokud argument předaný metodě s názvem neodpovídá `GetNumber` platnému indexu interního pole.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Volající metody pak používají `try-catch` `try-catch-finally` blok nebo pro zpracování vyvolané výjimky. Následující příklad zpracovává výjimku vyvolanou `GetNumber` metodou.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Opětovné vyvolání výjimky

`throw` lze také použít v `catch` bloku k opětovnému vyvolání výjimky zpracované v `catch` bloku.  V tomto případě `throw` nebere v úvahu operand výjimky. Je nejužitečnější, pokud metoda předává argumentu od volajícího k některé jiné metodě knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu. Například následující příklad znovu vyvolá výjimku <xref:System.NullReferenceException> , která je vyvolána při pokusu o načtení prvního znaku neinicializovaného řetězce.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Můžete také použít `throw e` syntaxi v `catch` bloku pro vytvoření instance nové výjimky, kterou předáte volajícímu. V tomto případě není zachováno trasování zásobníku původní výjimky, která je k dispozici z <xref:System.Exception.StackTrace> Vlastnosti.

## <a name="the-throw-expression"></a>`throw`Výraz

Počínaje jazykem C# 7,0 `throw` lze použít jako výraz i příkaz. To umožňuje vyvolání výjimky v kontextech, které byly dříve nepodporované. Zde jsou některé z nich:

- [podmíněný operátor](../operators/conditional-operator.md). Následující příklad používá `throw` výraz k vyvolání, <xref:System.ArgumentException> Pokud je metoda předána prázdnému poli řetězce. Před C# 7,0 se tato logika musí objevit v `if` / `else` příkazu.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [operátor slučování s hodnotou null](../operators/null-coalescing-operator.md). V následujícím příkladu `throw` se výraz používá s operátorem pro sjednocení s hodnotou null, který vyvolá výjimku, pokud je řetězec přiřazený `Name` vlastnosti `null` .

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- výraz [lambda](../operators/lambda-expressions.md) nebo metoda těle. Následující příklad znázorňuje metodu těle výrazu, která vyvolá výjimku, <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnotu není podporován.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Klíčová slova jazyka C#](index.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
