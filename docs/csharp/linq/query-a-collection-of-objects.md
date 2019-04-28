---
title: Dotazování na kolekci objektů (LINQ v JAZYKU C#)
description: Zjistěte, jak dát dotaz na kolekce pomocí jazyka LINQ v jazyce C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659807"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="71d38-103">Dotazování na kolekci objektů</span><span class="sxs-lookup"><span data-stu-id="71d38-103">Query a collection of objects</span></span>

<span data-ttu-id="71d38-104">Tento příklad ukazuje, jak provést jednoduchý dotaz přes seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="71d38-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="71d38-105">Každý `Student` objekt obsahuje některé základní informace o studenta a seznam, který představuje student získal skóre na čtyři zkoušky.</span><span class="sxs-lookup"><span data-stu-id="71d38-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="71d38-106">Tato aplikace slouží jako architektura pro mnoho příkladů v této části, které používají stejné `students` zdroj.</span><span class="sxs-lookup"><span data-stu-id="71d38-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71d38-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d38-107">Example</span></span>

<span data-ttu-id="71d38-108">Následující dotaz vrátí studenty, kteří obdrželi skóre 90 nebo vyšší na jejich první zkoušku.</span><span class="sxs-lookup"><span data-stu-id="71d38-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="71d38-109">Tento dotaz je záměrně jednoduchá umožňují snadno experimentovat.</span><span class="sxs-lookup"><span data-stu-id="71d38-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="71d38-110">Například můžete vyzkoušet další podmínky v `where` klauzuli, nebo použijte `orderby` klauzule řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="71d38-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d38-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71d38-111">See also</span></span>

- [<span data-ttu-id="71d38-112">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="71d38-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="71d38-113">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="71d38-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
