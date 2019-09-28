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
ms.openlocfilehash: 1e3f9ff82bdc4f35232c4ea1162050e216a9cc21
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353420"
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)

Signalizuje výskyt výjimky během provádění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e];
```

kde `e` je instance třídy odvozené z <xref:System.Exception?displayProperty=nameWithType>. Následující příklad používá příkaz `throw` k vyvolání <xref:System.IndexOutOfRangeException>, pokud argument předaný metodě s názvem `GetNumber` neodpovídá platnému indexu interního pole.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Volající metody pak používají blok `try-catch` nebo `try-catch-finally` pro zpracování vyvolané výjimky. Následující příklad zpracovává výjimku vyvolanou metodou `GetNumber`.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Opětovné vyvolání výjimky

`throw` lze také použít v bloku `catch` k opětovnému vyvolání výjimky zpracované v bloku `catch`.  V tomto případě `throw` nepřijímá operand výjimky. Je nejužitečnější, pokud metoda předává argumentu od volajícího k některé jiné metodě knihovny a metoda knihovny vyvolá výjimku, která musí být předána volajícímu. Například následující příklad znovu vyvolá <xref:System.NullReferenceException>, který je vyvolána při pokusu o načtení prvního znaku neinicializovaného řetězce.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Můžete také použít syntaxi `throw e` v bloku `catch` pro vytvoření instance nové výjimky, kterou předáte volajícímu. V tomto případě není zachováno trasování zásobníku původní výjimky, které je k dispozici z vlastnosti <xref:System.Exception.StackTrace>.

## <a name="the-throw-expression"></a>Výraz `throw`

Počínaje C# 7,0 `throw` lze použít jako výraz a také jako příkaz. To umožňuje vyvolání výjimky v kontextech, které byly dříve nepodporované. Mezi ně patří:

- [podmíněný operátor](../operators/conditional-operator.md). Následující příklad používá výraz `throw` k vyvolání <xref:System.ArgumentException>, pokud je metoda předána prázdnému poli řetězce. Před C# 7,0 se tato logika musí objevit v příkazu `if` @ no__t-2 @ no__t-3.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [operátor slučování s hodnotou null](../operators/null-coalescing-operator.md). V následujícím příkladu se výraz `throw` používá s operátorem pro sjednocení s hodnotou null k vyvolání výjimky, pokud je řetězec přiřazený vlastnosti `Name` `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- výraz [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metoda těle. Následující příklad znázorňuje metodu těle s výrazem, která vyvolá <xref:System.InvalidCastException>, protože převod na hodnotu <xref:System.DateTime> není podporován.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Klíčová slova jazyka C#](index.md)
- [Postupy: Explicitně vyvolávat výjimky @ no__t-0
