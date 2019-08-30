---
title: odkaz na C# vyvolání
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a9a235da06427e12bb5866a48f76f9c5896a572
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168750"
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)

Signalizuje výskyt výjimky během provádění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e]
```

kde `e` je instance třídy odvozené z <xref:System.Exception?displayProperty=nameWithType>. Následující příklad používá `throw` příkaz k <xref:System.IndexOutOfRangeException> vyvolání příkazu, pokud argument předaný metodě s názvem `GetNumber` neodpovídá platnému indexu interního pole.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Volající metody pak používají `try-catch` blok nebo `try-catch-finally` pro zpracování vyvolané výjimky. Následující příklad zpracovává výjimku vyvolanou `GetNumber` metodou.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Opětovné vyvolání výjimky

`throw`lze také použít v `catch` bloku k opětovnému vyvolání výjimky zpracované `catch` v bloku.  V tomto případě `throw` nebere v úvahu operand výjimky. Je nejužitečnější, pokud metoda předává argumentu od volajícího k některé jiné metodě knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu. Například následující příklad znovu vyvolá <xref:System.NullReferenceException> výjimku, která je vyvolána při pokusu o načtení prvního znaku neinicializovaného řetězce.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Můžete také použít `throw e` syntaxi `catch` v bloku pro vytvoření instance nové výjimky, kterou předáte volajícímu. V tomto případě není zachováno trasování zásobníku původní výjimky, která je k dispozici <xref:System.Exception.StackTrace> z vlastnosti.

## <a name="the-throw-expression"></a>`throw` Výraz

Počínaje C# 7,0 `throw` lze použít jako výraz i příkaz. To umožňuje vyvolání výjimky v kontextech, které byly dříve nepodporované. Zde jsou některé z nich:

- [podmíněný operátor](../operators/conditional-operator.md). Následující příklad používá `throw` výraz k <xref:System.ArgumentException> vyvolání, pokud je metoda předána prázdnému poli řetězce. Před C# 7,0 se tato logika musí objevit v `if` / `else` příkazu.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [operátor slučování s hodnotou null](../operators/null-coalescing-operator.md). V následujícím příkladu se `throw` výraz používá s operátorem pro sjednocení s hodnotou null, který vyvolá výjimku, pokud je `null`řetězec přiřazený `Name` vlastnosti.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- výraz [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metoda těle. Následující příklad znázorňuje metodu těle výrazu, která vyvolá výjimku <xref:System.InvalidCastException> , protože převod <xref:System.DateTime> na hodnotu není podporován.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a>specifikace jazyka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Klíčová slova jazyka C#](index.md)
- [Postupy: Explicitně vyvolat výjimky](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
