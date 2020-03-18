---
title: do - C# Reference
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713628"
---
# <a name="into-c-reference"></a>into (Referenční dokumentace jazyka C#)

Kontextové `into` klíčové slovo lze použít k vytvoření dočasného identifikátoru pro uložení výsledků [skupiny](group-clause.md), [spojení](join-clause.md) nebo [výběru](select-clause.md) klauzule do nového identifikátoru. Tento identifikátor může být sám generátor pro další příkazy dotazu. Při použití `group` v `select` klauzuli nebo se použití nového identifikátoru někdy označuje jako *pokračování*.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `into` klíčového slova k `fruitGroup` povolení dočasného identifikátoru, který má odvozený typ `IGrouping`. Pomocí identifikátoru můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu v každé skupině a vybrat pouze ty skupiny, které obsahují dvě nebo více slov.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Použití v `into` `group` klauzuli je nutné pouze v případě, že chcete provést další operace dotazu v každé skupině. Další informace naleznete v tématu [group clause](group-clause.md).

Příklad použití v klauzuli `join` naleznete v tématu `into` join [clause](join-clause.md).

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [group – klauzule](group-clause.md)
