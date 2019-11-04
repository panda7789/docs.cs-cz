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
ms.openlocfilehash: ccb1463db51510d275b7053955a0257bd4fe621e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422715"
---
# <a name="into-c-reference"></a>into (Referenční dokumentace jazyka C#)

Pomocí klíčového slova `into` kontextové lze vytvořit dočasný identifikátor pro uložení výsledků [skupiny](group-clause.md), [spojení](join-clause.md) nebo klauzule [Select](select-clause.md) do nového identifikátoru. Tento identifikátor může být generátorem pro další příkazy dotazu. Při použití v klauzuli `group` nebo `select` se použití nového identifikátoru někdy označuje jako *pokračování*.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití klíčového slova `into` pro povolení dočasného identifikátoru `fruitGroup`, který má odvozený typ `IGrouping`. Pomocí identifikátoru můžete vyvolat metodu <xref:System.Linq.Enumerable.Count%2A> v každé skupině a vybrat pouze skupiny, které obsahují dvě nebo více slov.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Použití `into` v klauzuli `group` je nutné pouze v případě, že chcete provést další operace dotazování u každé skupiny. Další informace naleznete v tématu [Group](group-clause.md)Group.

Příklad použití `into` v klauzuli `join` naleznete v tématu [klauzule JOIN](join-clause.md).

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [group – klauzule](group-clause.md)
