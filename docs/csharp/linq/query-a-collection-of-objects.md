---
title: Dotazování na kolekci objektů
description: Jak dotaz na kolekce.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282389"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="97808-103">Dotazování na kolekci objektů</span><span class="sxs-lookup"><span data-stu-id="97808-103">Query a collection of objects</span></span>
<span data-ttu-id="97808-104">Tento příklad ukazuje, jak provést jednoduchý dotaz pro seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="97808-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="97808-105">Každý `Student` objekt obsahuje některé základní informace o student a seznam, který představuje Studentova skóre na čtyři kontroly.</span><span class="sxs-lookup"><span data-stu-id="97808-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="97808-106">Tato aplikace slouží jako rozhraní pro mnoho příklady v této části, které používají stejné `students` zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="97808-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97808-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="97808-107">Example</span></span>  
 <span data-ttu-id="97808-108">Následující dotaz vrátí studenty, kteří obdrželi skóre 90 nebo vyšší na jejich první zkoušku.</span><span class="sxs-lookup"><span data-stu-id="97808-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="97808-109">Dotaz je umožnit experimentovat záměrně jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="97808-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="97808-110">Například můžete zkusit další podmínky v `where` klauzuli, nebo použijte `orderby` klauzule k řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="97808-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="97808-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="97808-111">See also</span></span>  
 [<span data-ttu-id="97808-112">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="97808-112">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="97808-113">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="97808-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
