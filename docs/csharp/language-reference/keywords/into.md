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
# <a name="into-c-reference"></a><span data-ttu-id="51cf1-102">into (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="51cf1-102">into (C# Reference)</span></span>

<span data-ttu-id="51cf1-103">Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátoru pro uložení výsledků [skupiny](group-clause.md), spojení nebo klauzule [Select](select-clause.md) do nového identifikátoru. [](join-clause.md) `into`</span><span class="sxs-lookup"><span data-stu-id="51cf1-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="51cf1-104">Tento identifikátor může být generátorem pro další příkazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="51cf1-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="51cf1-105">Při použití v `group` klauzuli OR `select` se použití nového identifikátoru někdy označuje jako *pokračování*.</span><span class="sxs-lookup"><span data-stu-id="51cf1-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="51cf1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="51cf1-106">Example</span></span>

<span data-ttu-id="51cf1-107">Následující příklad ukazuje použití `into` klíčového slova k povolení dočasného identifikátoru `fruitGroup` , který má odvozený typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="51cf1-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="51cf1-108">Pomocí identifikátoru můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu pro každou skupinu a vybrat pouze skupiny, které obsahují dvě nebo více slov.</span><span class="sxs-lookup"><span data-stu-id="51cf1-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="51cf1-109">Použití `into` klauzule`group` in je nezbytné pouze v případě, že chcete provést další operace dotazování u každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="51cf1-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="51cf1-110">Další informace naleznete v tématu [Group](group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="51cf1-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="51cf1-111">Příklad použití `into` `join` klauzule v klauzuli naleznete v tématu [klauzule JOIN](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="51cf1-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51cf1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51cf1-112">See also</span></span>

- [<span data-ttu-id="51cf1-113">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="51cf1-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="51cf1-114">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="51cf1-114">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="51cf1-115">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="51cf1-115">group clause</span></span>](group-clause.md)
