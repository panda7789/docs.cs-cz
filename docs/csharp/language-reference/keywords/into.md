---
description: Reference into-C#
title: Reference into-C#
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134520"
---
# <a name="into-c-reference"></a>into (Referenční dokumentace jazyka C#)

`into`Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátoru pro uložení výsledků [skupiny](group-clause.md), [spojení](join-clause.md) nebo klauzule [Select](select-clause.md) do nového identifikátoru. Tento identifikátor může být generátorem pro další příkazy dotazu. Při použití v `group` klauzuli OR se `select` použití nového identifikátoru někdy označuje jako *pokračování*.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `into` klíčového slova k povolení dočasného identifikátoru, `fruitGroup` který má odvozený typ `IGrouping` . Pomocí identifikátoru můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu pro každou skupinu a vybrat pouze skupiny, které obsahují dvě nebo více slov.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Použití `into` `group` klauzule in je nezbytné pouze v případě, že chcete provést další operace dotazování u každé skupiny. Další informace naleznete v tématu [Group](group-clause.md)Group.

Příklad použití `into` `join` klauzule v klauzuli naleznete v tématu [klauzule JOIN](join-clause.md).

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyku C#](../../linq/index.md)
- [group – klauzule](group-clause.md)
