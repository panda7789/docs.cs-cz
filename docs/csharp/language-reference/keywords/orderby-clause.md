---
title: klauzule orderby - C# Reference
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173572"
---
# <a name="orderby-clause-c-reference"></a>orderby – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) mají být seřazeny vzestupně nebo sestupně. Pro provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů. Řazení se provádí výchozí porovnávání pro typ prvku. Výchozí pořadí řazení je vzestupně. Můžete také zadat vlastní porovnávání. Je však k dispozici pouze pomocí syntaxe založené na metodě. Další informace naleznete v [tématu Řazení dat](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Příklad

V následujícím příkladu první dotaz seřadí slova v abecedním pořadí od A a druhý dotaz seřadí stejná slova v sestupném pořadí. (Klíčové `ascending` slovo je výchozí hodnotou řazení a lze jej vynechat.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Příklad

Následující příklad provádí primární řazení na příjmení studentů a potom sekundární řazení na jejich křestní jména.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Poznámky

V době kompilace klauzule `orderby` je přeložen <xref:System.Linq.Enumerable.OrderBy%2A> a volání metody. Více klíčů `orderby` v klauzuli přeložit volání <xref:System.Linq.Enumerable.ThenBy%2A> metody.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [group – klauzule](group-clause.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
