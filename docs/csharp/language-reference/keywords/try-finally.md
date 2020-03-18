---
title: try-finally - C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713011"
---
# <a name="try-finally-c-reference"></a>try-finally (Referenční dokumentace jazyka C#)

Pomocí `finally` bloku můžete vyčistit všechny prostředky, které jsou přiděleny v [bloku try,](try-catch.md) a můžete spustit `try` kód i v případě, že dojde k výjimce v bloku. Obvykle příkazy `finally` bloku spustit při ovládacíprvek `try` opustí příkaz. K převodu ovládacího prvku může dojít v důsledku `break` `continue`normálního spuštění, provedení , , `goto`nebo `return` příkazu `try` nebo šíření výjimky z příkazu.

V rámci zpracované výjimky je zaručeno spuštění přidruženého `finally` bloku. Pokud je však výjimka neošetřena, je spuštění `finally` bloku závislé na způsobu, jakým je spuštěna operace unwind výjimky. To zase závisí na tom, jak je počítač nastaven.

Obvykle při neošetřené výjimky ukončí aplikaci, zda `finally` je či není blok je spuštěn není důležité. Však pokud máte příkazy v `finally` bloku, který musí být spuštěn i `catch` v `try` - `finally` této situaci, jedním z řešení je přidat blok do příkazu. Alternativně můžete zachytit výjimku, která může `try` být vyvolána v bloku příkazu `try` - `finally` vyšší zásobníku volání. To znamená, že můžete zachytit výjimku v metodě, která volá metodu, která obsahuje `try` - `finally` příkaz, nebo v metodě, která volá tuto metodu, nebo v libovolné metodě v zásobníku volání. Pokud výjimka není zachycena, `finally` spuštění bloku závisí na tom, zda se operační systém rozhodne aktivovat operaci unwind výjimky.

## <a name="example"></a>Příklad

V následujícím příkladu neplatný příkaz `System.InvalidCastException` převodu způsobí výjimku. Výjimka není zpracována.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

V následujícím příkladu je `TryCast` výjimka z metody zachycena v metodě dále v zásobníku volání.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Další informace `finally`o tématu [naleznete v tématu try-catch-finally](try-catch-finally.md).

C# také obsahuje [using příkaz](using-statement.md), který <xref:System.IDisposable> poskytuje podobné funkce pro objekty ve vhodné syntaxi.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [try statement](~/_csharplang/spec/statements.md#the-try-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [try, throw a catch – příkazy (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Postupy: Explicitní generování výjimek](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
