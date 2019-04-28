---
title: do - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: b209062a2a3e563ea8e70cb7883d9bbfa3662231
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661344"
---
# <a name="into-c-reference"></a><span data-ttu-id="a4963-102">into (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a4963-102">into (C# Reference)</span></span>

<span data-ttu-id="a4963-103">`into` Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátor pro ukládání výsledků [skupiny](group-clause.md), [spojení](join-clause.md) nebo [vyberte](select-clause.md) klauzuli do nového identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a4963-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="a4963-104">Tento identifikátor může být sám generátor pro příkazy další dotaz.</span><span class="sxs-lookup"><span data-stu-id="a4963-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="a4963-105">Při použití `group` nebo `select` klauzule, použijte nový identifikátor se někdy označuje jako *pokračování*.</span><span class="sxs-lookup"><span data-stu-id="a4963-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="a4963-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4963-106">Example</span></span>

<span data-ttu-id="a4963-107">Následující příklad ukazuje použití `into` – klíčové slovo umožňující dočasné identifikátor `fruitGroup` která má odvozený typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="a4963-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="a4963-108">S použitím identifikátoru, můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metodu na každý skupinu a vybrat jenom skupiny, které obsahují dva nebo více slov.</span><span class="sxs-lookup"><span data-stu-id="a4963-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="a4963-109">Použití `into` v `group` klauzule je potřeba, pouze pokud budete chtít provádět operace dalšího dotazu pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="a4963-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="a4963-110">Další informace najdete v tématu [group – klauzule](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a4963-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="a4963-111">Příklad použití `into` v `join` klauzule, naleznete v tématu [klauzule join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a4963-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4963-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4963-112">See also</span></span>

- [<span data-ttu-id="a4963-113">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a4963-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="a4963-114">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="a4963-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="a4963-115">group – klauzule</span><span class="sxs-lookup"><span data-stu-id="a4963-115">group clause</span></span>](group-clause.md)
