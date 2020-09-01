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
# <a name="into-c-reference"></a><span data-ttu-id="cc4dd-103">into (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cc4dd-103">into (C# Reference)</span></span>

<span data-ttu-id="cc4dd-104">`into`Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátoru pro uložení výsledků [skupiny](group-clause.md), [spojení](join-clause.md) nebo klauzule [Select](select-clause.md) do nového identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-104">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="cc4dd-105">Tento identifikátor může být generátorem pro další příkazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-105">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="cc4dd-106">Při použití v `group` klauzuli OR se `select` použití nového identifikátoru někdy označuje jako *pokračování*.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-106">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="cc4dd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc4dd-107">Example</span></span>

<span data-ttu-id="cc4dd-108">Následující příklad ukazuje použití `into` klíčového slova k povolení dočasného identifikátoru, `fruitGroup` který má odvozený typ `IGrouping` .</span><span class="sxs-lookup"><span data-stu-id="cc4dd-108">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="cc4dd-109">Pomocí identifikátoru můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu pro každou skupinu a vybrat pouze skupiny, které obsahují dvě nebo více slov.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-109">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="cc4dd-110">Použití `into` `group` klauzule in je nezbytné pouze v případě, že chcete provést další operace dotazování u každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-110">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="cc4dd-111">Další informace naleznete v tématu [Group](group-clause.md)Group.</span><span class="sxs-lookup"><span data-stu-id="cc4dd-111">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="cc4dd-112">Příklad použití `into` `join` klauzule v klauzuli naleznete v tématu [klauzule JOIN](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cc4dd-112">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc4dd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc4dd-113">See also</span></span>

- [<span data-ttu-id="cc4dd-114">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="cc4dd-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="cc4dd-115">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="cc4dd-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="cc4dd-116">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="cc4dd-116">group clause</span></span>](group-clause.md)
