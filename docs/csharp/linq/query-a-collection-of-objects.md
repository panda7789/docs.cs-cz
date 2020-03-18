---
title: Dotaz na kolekci objektů (LINQ v c#)
description: Zjistěte, jak kolekce dotazů pomocí LINQ v C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659807"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="0777f-103">Dotazování na kolekci objektů</span><span class="sxs-lookup"><span data-stu-id="0777f-103">Query a collection of objects</span></span>

<span data-ttu-id="0777f-104">Tento příklad ukazuje, jak provést jednoduchý `Student` dotaz přes seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="0777f-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="0777f-105">Každý `Student` objekt obsahuje některé základní informace o studentovi a seznam, který představuje skóre studenta na čtyřech zkouškách.</span><span class="sxs-lookup"><span data-stu-id="0777f-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="0777f-106">Tato aplikace slouží jako rámec pro mnoho dalších příkladů `students` v této části, které používají stejný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="0777f-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0777f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0777f-107">Example</span></span>

<span data-ttu-id="0777f-108">Následující dotaz vrátí studentům, kteří při první zkoušce obdrželi skóre 90 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="0777f-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="0777f-109">Tento dotaz je záměrně jednoduché, aby vám umožní experimentovat.</span><span class="sxs-lookup"><span data-stu-id="0777f-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="0777f-110">Můžete například vyzkoušet další `where` podmínky v klauzuli nebo použít klauzuli `orderby` k řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="0777f-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0777f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0777f-111">See also</span></span>

- [<span data-ttu-id="0777f-112">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="0777f-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="0777f-113">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="0777f-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
