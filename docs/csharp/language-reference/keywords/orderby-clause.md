---
title: orderby – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217435"
---
# <a name="orderby-clause-c-reference"></a>orderby – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu `orderby` klauzule způsobí, že vrácená sekvence nebo dílčí sekvenci (skupiny), který se má seřadit ve vzestupném nebo sestupném pořadí. Aby bylo možné provést jednu nebo více operací sekundární řazení lze zadat více klíčů. Řazení se provádí pomocí výchozí porovnávací metody pro typ prvku. Je výchozí pořadí řazení vzestupně. Můžete také určit vlastní porovnávací metody. Je však pouze k dispozici pomocí syntaxe založených na volání metody. Další informace najdete v tématu [řazení dat](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Příklad

V následujícím příkladu seřadí slova v abecedním pořadí A od prvního dotazu a druhý dotaz seřadí stejná slova v sestupném pořadí. ( `ascending` – Klíčové slovo je výchozí hodnota řazení a lze vynechat.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Příklad

Následující příklad provádí primární řazení podle příjmení studenty a sekundární řazení na jejich jména.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Poznámky

V době kompilace `orderby` přeložen na volání <xref:System.Linq.Enumerable.OrderBy%2A> metody. Více klíčů `orderby` klauzule přeložit do <xref:System.Linq.Enumerable.ThenBy%2A> volání metody.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [group – klauzule](group-clause.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)