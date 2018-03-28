---
title: Dotazování na kolekci objektů
description: Jak dotaz na kolekce.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="99676-104">Dotazování na kolekci objektů</span><span class="sxs-lookup"><span data-stu-id="99676-104">Query a collection of objects</span></span>
<span data-ttu-id="99676-105">Tento příklad ukazuje, jak provést jednoduchý dotaz pro seznam `Student` objekty.</span><span class="sxs-lookup"><span data-stu-id="99676-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="99676-106">Každý `Student` objekt obsahuje některé základní informace o student a seznam, který představuje Studentova skóre na čtyři kontroly.</span><span class="sxs-lookup"><span data-stu-id="99676-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="99676-107">Tato aplikace slouží jako rozhraní pro mnoho příklady v této části, které používají stejné `students` zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="99676-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99676-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="99676-108">Example</span></span>  
 <span data-ttu-id="99676-109">Následující dotaz vrátí studenty, kteří obdrželi skóre 90 nebo vyšší na jejich první zkoušku.</span><span class="sxs-lookup"><span data-stu-id="99676-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="99676-110">Dotaz je umožnit experimentovat záměrně jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="99676-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="99676-111">Například můžete zkusit další podmínky v `where` klauzuli, nebo použijte `orderby` klauzule k řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="99676-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="99676-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="99676-112">See also</span></span>  
 [<span data-ttu-id="99676-113">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="99676-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="99676-114">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="99676-114">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
