---
title: throw – C# odkaz
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
ms.openlocfilehash: d6911ff96ca847f554e9b615aba6ab83a212efee
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125990"
---
# <a name="throw-c-reference"></a>throw (Referenční dokumentace jazyka C#)

Signály výskyt výjimku při provádění programu.  
  
## <a name="remarks"></a>Poznámky

Syntaxe `throw` je:

```csharp
throw [e]
```

kde `e` je instancí třídy odvozené od <xref:System.Exception?displayProperty=nameWithType>. V následujícím příkladu `throw` příkaz throw <xref:System.IndexOutOfRangeException> Pokud argument předaný do metodu s názvem `GetNumber` neodpovídá platný index interní pole.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Pak pomocí metody volající `try-catch` nebo `try-catch-finally` bloku zpracovat vyvolanou výjimku. V následujícím příkladu zpracovává výjimky vyvolané `GetNumber` metody.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Opětovné vyvolání výjimky

`throw` Můžete také použít v `catch` pro opětovné vyvolání výjimky zpracovávány v `catch` bloku.  V takovém případě `throw` nepřijímá operand výjimky. To je nejužitečnější, když metoda předává na argument z volající do některé jiné metody knihovny a knihovny metoda vyvolá výjimku, která musí být předán volajícímu. Například v následujícím příkladu je znovu vyvolá <xref:System.NullReferenceException> , která je vyvolána při pokusu o načtení první znak neinicializovaný řetězec.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Můžete také použít `throw e` syntaxe v poznámce `catch` bloku pro vytvoření instance novou výjimku, můžete předat volajícího. V takovém případě původní výjimky, trasování zásobníku, což je k dispozici <xref:System.Exception.StackTrace> vlastností, nejsou uchována.

## <a name="the-throw-expression"></a>`throw` Výraz

Od verze C# 7.0, `throw` lze použít jako výraz, stejně jako příkaz. To umožňuje výjimka vyvolána v kontextech, které byly dříve nepodporovaný. Zde jsou některé z nich:

- [podmiňovací operátor](../operators/conditional-operator.md). Následující příklad používá `throw` výraz throw <xref:System.ArgumentException> metodu je předán prázdný řetězec pole. Před C# 7.0, by bylo potřeba joinkind tuto logiku `if` / `else` příkazu.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [operátoru nulového sjednocení](../operators/null-coalescing-operator.md). V následujícím příkladu `throw` použit výraz pomocí operátoru nulového sjednocení vyvolá výjimku, pokud se přiřadí řetězec `Name` vlastnost `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- s výrazem v těle [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nebo metody. Následující příklad ukazuje metodu s výrazem v těle, která se vyvolá <xref:System.InvalidCastException> protože převod na <xref:System.DateTime> hodnota není podporována.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a>specifikace jazyka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Try, catch a throw – příkazy v jazyce C++](try-catch.md)
- [Klíčová slova jazyka C#](index.md)
- [Příkazy zpracování výjimek](exception-handling-statements.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
