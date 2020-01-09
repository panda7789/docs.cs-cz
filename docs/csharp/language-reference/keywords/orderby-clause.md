---
title: Klauzule OrderBy – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: d88b2b40f63f0616cfd54e8abb62f1bc2183f776
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713301"
---
# <a name="orderby-clause-c-reference"></a>orderby – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu klauzule `orderby` způsobí, že vrácená sekvence nebo dílčí sekvence (skupina) bude seřazena ve vzestupném nebo sestupném pořadí. K provedení jedné nebo více sekundárních operací řazení lze zadat více klíčů. Řazení je provedeno pomocí výchozí porovnávací metody pro typ elementu. Výchozí pořadí řazení je vzestupné. Můžete také zadat vlastní porovnávací metodu. Je však k dispozici pouze pomocí syntaxe založené na metodě. Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Příklad

V následujícím příkladu první dotaz seřadí slova v abecedním pořadí začínajícím na a druhý dotaz seřadí stejná slova v sestupném pořadí. (Klíčové slovo `ascending` je výchozí hodnota řazení a může být vynechána.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Příklad

Následující příklad provádí primární řazení pro příjmení studentů a pak sekundární řazení podle jejich křestních jmen.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Poznámky

V době kompilace je klauzule `orderby` přeložena na volání metody <xref:System.Linq.Enumerable.OrderBy%2A>. Více klíčů v klauzuli `orderby` se přeloží na <xref:System.Linq.Enumerable.ThenBy%2A> volání metod.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [ (LINQ)](../../linq/index.md)
- [group – klauzule](group-clause.md)
- [Začínáme s dotazy LINQ v jazyce C#](/dotnet/csharp/programming-guide/concepts/linq/)
