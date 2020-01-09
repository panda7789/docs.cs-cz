---
title: try-finally- C# reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713011"
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)

Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v bloku [Try](try-catch.md) , a můžete kód spustit i v případě, že dojde k výjimce v bloku `try`. Příkazy `finally` bloku jsou obvykle spouštěny, když ovládací prvek opustí příkaz `try`. Přenos řízení může nastat v důsledku normálního spuštění, spuštění `break`, `continue`, `goto`nebo `return`ho příkazu nebo šíření výjimky z příkazu `try`.

V rámci ošetřené výjimky je zaručeno spuštění přidruženého `finally`ho bloku. Nicméně pokud je výjimka Neošetřená, spuštění bloku `finally` závisí na tom, jak je spuštěna operace unwind výjimky. To znamená, že je závislý na tom, jak je počítač nastavený.

Obvykle, pokud Neošetřená výjimka ukončí aplikaci, bez ohledu na to, zda je spuštěn blok `finally`, není důležité. Nicméně pokud máte příkazy v bloku `finally`, které musí být spuštěny i v takové situaci, jedním z řešení je přidání bloku `catch` do příkazu `try`-`finally`. Alternativně můžete zachytit výjimku, která může být vyvolána v `try` bloku `try`-příkazu `finally` výše v zásobníku volání. To znamená, že výjimku můžete zachytit v metodě, která volá metodu, která obsahuje příkaz `try`-`finally` nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání. Pokud není výjimka zachycena, provedení `finally`ho bloku závisí na tom, zda se rozhodne operační systém aktivovat výjimku unwind operace.

## <a name="example"></a>Příklad

V následujícím příkladu neplatný příkaz převodu způsobí výjimku `System.InvalidCastException`. Výjimka je Neošetřená.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

V následujícím příkladu je zachycena výjimka z metody `TryCast` v metodě dále v zásobníku volání.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Další informace o `finally`najdete v tématu [try-catch-finally](try-catch-finally.md).

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
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
