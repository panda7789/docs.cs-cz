---
title: Zpracování výjimek ve výrazech dotazů (LINQ v JAZYKU C#)
description: Informace o zpracování výjimek ve výrazech dotazů LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 344d11129814516a5ed3dcf0eba73a5ecbb96981
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403836"
---
# <a name="handle-exceptions-in-query-expressions"></a>Zpracování výjimek ve výrazech dotazů

Je možné volat jakékoli metody v kontextu výrazu dotazu. Doporučujeme však, že byste se vyhnout voláním jakékoli metody ve výrazu dotazu, můžete vytvořit vedlejší účinek, jako je například změna obsahu zdroje dat nebo došlo k výjimce. Tento příklad ukazuje, jak se vyhnout vyvolání výjimky při volání metody ve výrazu dotazu, aniž by byla porušena obecné pokyny .NET pro zpracování výjimek. Tyto pokyny stavu, která je akceptovatelná podle zachycení konkrétní výjimky, když víte, proč je vyvolána v daném kontextu. Další informace najdete v tématu [osvědčené postupy pro výjimky](../../standard/exceptions/best-practices-for-exceptions.md).

Poslední příklad ukazuje, jak zpracovat případy, když musíte vyvolat výjimku během provádění dotazu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přesunout kód mimo výraz dotazu zpracování výjimek. To je možné jenom Pokud metoda nezávisí na žádné proměnné pro dotaz místní.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Příklad

V některých případech může být nejlepší odpověď na výjimku, která je vyvolána z v rámci dotazu okamžitě zastavit provádění dotazu. Následující příklad ukazuje, jak zpracovat výjimky, které mohou být vyvolány z uvnitř za tělem dotazu. Předpokládejme, že `SomeMethodThatMightThrow` může potenciálně způsobit výjimku, která vyžaduje spuštění dotazu se zastavit.

Všimněte si, že `try` obklopuje bloku `foreach` smyčky a ne samotný dotaz. Je to proto, `foreach` smyčky je bod, ve kterém ve skutečnosti spuštění dotazu. Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Viz také:

[LINQ (Language Integrated Query)](index.md)  
