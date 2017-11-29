---
title: "into (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords: into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a><span data-ttu-id="b9780-102">into (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b9780-102">into (C# Reference)</span></span>
<span data-ttu-id="b9780-103">`into` Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátor k ukládání výsledků [skupiny](../../../csharp/language-reference/keywords/group-clause.md), [spojení](../../../csharp/language-reference/keywords/join-clause.md) nebo [vyberte](../../../csharp/language-reference/keywords/select-clause.md) klauzule do nový identifikátor.</span><span class="sxs-lookup"><span data-stu-id="b9780-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="b9780-104">Tento identifikátor může být sám generátor pro příkazy další dotaz.</span><span class="sxs-lookup"><span data-stu-id="b9780-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="b9780-105">Při použití v `group` nebo `select` klauzuli použití nový identifikátor se někdy označuje jako *pokračování*.</span><span class="sxs-lookup"><span data-stu-id="b9780-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9780-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9780-106">Example</span></span>  
 <span data-ttu-id="b9780-107">Následující příklad ukazuje použití `into` – klíčové slovo povolit dočasné identifikátor `fruitGroup` jehož typ odvozené `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="b9780-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="b9780-108">Pomocí identifikátor můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metoda na každé skupiny a vybrat jenom skupiny, které obsahují dvě nebo více slov.</span><span class="sxs-lookup"><span data-stu-id="b9780-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 <span data-ttu-id="b9780-109">Použití `into` v `group` klauzule je potřeba, pouze pokud chcete provádět operace další dotaz pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="b9780-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="b9780-110">Další informace najdete v tématu [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b9780-110">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="b9780-111">Příklad použití `into` v `join` klauzule, najdete v části [klauzuli join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b9780-111">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9780-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9780-112">See Also</span></span>  
 [<span data-ttu-id="b9780-113">Klíčová slova dotazu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b9780-113">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="b9780-114">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="b9780-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="b9780-115">Group – klauzule</span><span class="sxs-lookup"><span data-stu-id="b9780-115">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)
