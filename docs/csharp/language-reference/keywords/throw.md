---
title: throw (Referenční dokumentace jazyka C#)
ms.date: 03/02/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 088a8e70c5aaaae6f833f12cad1052c30fbb6bfa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)
Signály výskytem výjimku při spuštění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e]
```
kde `e` je instance třídy odvozené od <xref:System.Exception?displayProperty=nameWithType>. Následující příklad používá `throw` příkaz má být vyvolána <xref:System.IndexOutOfRangeException> Pokud argument předaný metodu s názvem `GetNumber` neodpovídá platný index interní pole.

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Metoda pak volající `try-catch` nebo `try-catch-finally` bloku pro zpracování vyvolaná výjimka. Následující příklad zpracovává výjimky vyvolané `GetNumber` metoda.

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Znovu došlo k výjimce

`throw` Můžete také použít v `catch` zpracovává blok k znovu vyvolat výjimku při `catch` bloku.  V takovém případě `throw` nevyžaduje operand výjimka. Je velmi užitečné při metodu předá na argument z volající nějaké jiné metody knihovny a knihovna metoda vyvolá výjimku, která musí být předán volajícímu. Například v následujícím příkladu je znovu vyvolá <xref:System.NullReferenceException> , je vyvolána při pokusu o načtení první znak řetězec Neinicializovaný. 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Můžete také `throw e` syntaxi `catch` bloku se vytvořit novou výjimku, kterou předáte volajícímu. V tomto případě trasování zásobníku pro původní výjimka, která je k dispozici z <xref:System.Exception.StackTrace> vlastnost, není zachována.
 
## <a name="the-throw-expression"></a>`throw` Výraz

Od verze jazyka C# 7.0, `throw` lze použít jako výraz, jakož i příkaz. To umožňuje výjimku vyvolání v kontextu, které byly dříve nepodporovaný. Mezi ně patří:

- [Podmíněný operátor](../operators/conditional-operator.md). Následující příklad používá `throw` výraz, který se throw <xref:System.ArgumentException> Pokud metoda je předán prázdný řetězec pole. Před C# 7.0, by potřeba se zobrazí v této logiky `if` / `else` příkaz.

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [operátor slučování null](../operators/null-conditional-operator.md). V následujícím příkladu `throw` výraz se používá s operátorem se slučování null vyvolá výjimku, pokud řetězec přiřazené `Name` vlastnost je `null`.
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- výrazu vozidlo [lambda](../../lambda-expressions.md) nebo metoda. Následující příklad ukazuje metodu vozidlo výrazu, která způsobí výjimku, <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnota není podporována.
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Try, catch a throw – příkazy v jazyce C++](../../../csharp/language-reference/keywords/try-catch.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
