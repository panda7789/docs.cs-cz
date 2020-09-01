---
description: orderby – klauzule – reference jazyka C#
title: orderby – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142346"
---
# <a name="orderby-clause-c-reference"></a>orderby – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) bude seřazena ve vzestupném nebo sestupném pořadí. K provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů. Řazení je provedeno pomocí výchozí porovnávací metody pro typ elementu. Výchozí pořadí řazení je vzestupné. Můžete také zadat vlastní porovnávací metodu. Je však k dispozici pouze pomocí syntaxe založené na metodě. Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Příklad

V následujícím příkladu první dotaz seřadí slova v abecedním pořadí začínajícím na a druhý dotaz seřadí stejná slova v sestupném pořadí. ( `ascending` Klíčové slovo je výchozí hodnota řazení a může být vynecháno.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Příklad

Následující příklad provádí primární řazení pro příjmení studentů a pak sekundární řazení podle jejich křestních jmen.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Poznámky

V době kompilace `orderby` je klauzule přeložena na volání <xref:System.Linq.Enumerable.OrderBy%2A> metody. Více klíčů v `orderby` klauzuli je přeloženo na <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyku C#](../../linq/index.md)
- [group – klauzule](group-clause.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
