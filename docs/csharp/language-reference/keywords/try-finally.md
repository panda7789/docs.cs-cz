---
description: try-finally-reference jazyka C#
title: try-finally-reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141969"
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)

Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v bloku [Try](try-catch.md) , a můžete kód spustit i v případě, že v bloku dojde k výjimce `try` . Obvykle jsou příkazy `finally` bloku spouštěny, když ovládací prvek opustí `try` příkaz. Přenos řízení může nastat v důsledku normálního spuštění, provedení `break` příkazu,, `continue` `goto` nebo `return` nebo šíření výjimky z `try` příkazu.

V rámci ošetřené výjimky `finally` je zaručeno spuštění přidruženého bloku. Nicméně pokud je výjimka Neošetřená, `finally` je spuštění bloku závislé na tom, jak je spuštěna operace unwind výjimky. To znamená, že je závislý na tom, jak je počítač nastavený.

Obvykle, pokud Neošetřená výjimka ukončí aplikaci, bez ohledu na to, zda je `finally` blok spuštěn, není důležité. Nicméně pokud máte příkazy v `finally` bloku, který musí být spuštěn dokonce i v takovém případě, jedním řešením je přidání `catch` bloku do `try` - `finally` příkazu. Alternativně můžete zachytit výjimku, která může být vyvolána v `try` bloku `try` - `finally` příkazu výše v zásobníku volání. To znamená, že výjimku můžete zachytit v metodě, která volá metodu, která obsahuje `try` - `finally` příkaz, nebo v metodě, která volá tuto metodu, nebo v jakékoli metodě v zásobníku volání. Pokud není výjimka zachycena, spuštění `finally` bloku závisí na tom, zda se rozhodne operační systém aktivovat výjimku unwind operace.

## <a name="example"></a>Příklad

V následujícím příkladu je neplatný příkaz převodu způsobil `System.InvalidCastException` výjimku. Výjimka je Neošetřená.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

V následujícím příkladu je výjimka z `TryCast` metody zachycena v metodě dále v zásobníku volání.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Další informace o `finally` naleznete v tématu [try-catch-finally](try-catch-finally.md).

Jazyk C# obsahuje také [příkaz using](using-statement.md), který poskytuje podobné funkce pro <xref:System.IDisposable> objekty ve vhodné syntaxi.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [Try příkazu](~/_csharplang/spec/statements.md#the-try-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
