---
title: try-finally- C# reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: a8d18a6ae8b3f8f6cde76b1b296ac6a317ca1ed1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168581"
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)

Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v bloku [Try](try-catch.md) , a můžete kód spustit i v případě, že v `try` bloku dojde k výjimce. Obvykle jsou příkazy `finally` bloku spouštěny, když ovládací prvek `try` opustí příkaz. Přenos řízení může nastat v důsledku `break`normálního spuštění, provedení `try` příkazu `goto`, `continue`, nebo `return` nebo šíření výjimky z příkazu.

V rámci ošetřené výjimky je zaručeno spuštění přidruženého `finally` bloku. Nicméně pokud je výjimka Neošetřená, je spuštění `finally` bloku závislé na tom, jak je spuštěna operace unwind výjimky. To znamená, že je závislý na tom, jak je počítač nastavený.

Obvykle, pokud Neošetřená výjimka ukončí aplikaci, bez ohledu na `finally` to, zda je blok spuštěn, není důležité. Nicméně pokud máte `finally` příkazy v bloku, který musí být spuštěn dokonce i v takovém případě, jedním řešením je `catch` Přidání bloku do `try` - `finally` příkazu. Alternativně můžete zachytit výjimku, která může být vyvolána `try` v bloku `try` - `finally` příkazu výše v zásobníku volání. To znamená, že výjimku můžete zachytit v metodě, která volá metodu, která obsahuje `try` - `finally` příkaz, nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání. Pokud není výjimka zachycena, spuštění `finally` bloku závisí na tom, zda se rozhodne operační systém aktivovat výjimku unwind operace.

## <a name="example"></a>Příklad

V následujícím příkladu je neplatný příkaz převodu způsobil `System.InvalidCastException` výjimku. Výjimka je Neošetřená.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

V následujícím příkladu je výjimka z `TryCast` metody zachycena v metodě dále v zásobníku volání.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Další informace o `finally`naleznete v tématu [try-catch-finally](try-catch-finally.md).

C#obsahuje také [příkaz using](using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty ve vhodné syntaxi.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkaz try](~/_csharplang/spec/statements.md#the-try-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Postupy: Explicitně vyvolat výjimky](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
