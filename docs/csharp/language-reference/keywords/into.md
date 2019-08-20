---
title: C# odkaz na
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608635"
---
# <a name="into-c-reference"></a>into (Referenční dokumentace jazyka C#)

Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátoru pro uložení výsledků [skupiny](group-clause.md), spojení nebo klauzule [Select](select-clause.md) do nového identifikátoru. [](join-clause.md) `into` Tento identifikátor může být generátorem pro další příkazy dotazu. Při použití v `group` klauzuli OR `select` se použití nového identifikátoru někdy označuje jako *pokračování*.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `into` klíčového slova k povolení dočasného identifikátoru `fruitGroup` , který má odvozený typ `IGrouping`. Pomocí identifikátoru můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu pro každou skupinu a vybrat pouze skupiny, které obsahují dvě nebo více slov.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Použití `into` klauzule`group` in je nezbytné pouze v případě, že chcete provést další operace dotazování u každé skupiny. Další informace naleznete v tématu [Group](group-clause.md)Group.

Příklad použití `into` `join` klauzule v klauzuli naleznete v tématu [klauzule JOIN](join-clause.md).

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [Výrazy dotazů LINQ](../../programming-guide/linq-query-expressions/index.md)
- [group – klauzule](group-clause.md)
