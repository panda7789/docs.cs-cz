---
title: Zpracování výjimek ve výrazech dotazů (LINQ v c#)
description: Zjistěte, jak zpracovat výjimky ve výrazech dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688498"
---
# <a name="handle-exceptions-in-query-expressions"></a>Zpracování výjimek ve výrazech dotazů

Je možné volat libovolnou metodu v kontextu výrazu dotazu. Doporučujeme však vyhnout se volání jakékoli metody ve výrazu dotazu, který může vytvořit vedlejší účinek, jako je například úprava obsahu zdroje dat nebo vyvolání výjimky. Tento příklad ukazuje, jak se vyhnout vyvolání výjimek při volání metod ve výrazu dotazu bez porušení obecných pokynů rozhraní .NET pro zpracování výjimek. Tyto pokyny uvádějí, že je přijatelné zachytit konkrétní výjimku, když pochopíte, proč je vyvolána v daném kontextu. Další informace naleznete v [tématu Doporučené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).

Poslední příklad ukazuje, jak zpracovat tyto případy, kdy je nutné vyvolat výjimku při provádění dotazu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přesunout kód zpracování výjimek mimo výraz dotazu. To je možné pouze v případě, že metoda nezávisí na žádné proměnné místní dotazu.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Příklad

V některých případech nejlepší odpověď na výjimku, která je vyvolána z v rámci dotazu může být okamžité zastavení provádění dotazu. Následující příklad ukazuje, jak zpracovat výjimky, které mohou být vyvolány z uvnitř těla dotazu. Předpokládejme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu zastavit.

Všimněte `try` si, že `foreach` blok obklopuje smyčku a ne samotný dotaz. Důvodem je, `foreach` že smyčka je bod, ve kterém je dotaz skutečně spuštěn. Další informace naleznete [v tématu Úvod do linq dotazy](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
