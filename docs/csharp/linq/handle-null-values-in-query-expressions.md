---
title: "Zpracování hodnot null ve výrazech dotazů"
description: "Postupy: zpracování hodnot null ve výrazech dotazů."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="7f3cd-104">Zpracování hodnot null ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="7f3cd-104">Handle null values in query expressions</span></span>

<span data-ttu-id="7f3cd-105">Tento příklad ukazuje postup zpracování možných hodnot null ve zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="7f3cd-106">Kolekci objektů, jako <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnoty se [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="7f3cd-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="7f3cd-107">Pokud zdrojové kolekci je null nebo obsahuje element, jehož hodnota je null a dotaz nezpracovává hodnoty null, <xref:System.NullReferenceException> bude vyvolána při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f3cd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f3cd-108">Example</span></span>

 <span data-ttu-id="7f3cd-109">Můžete obranu kódu předejdete výjimka odkazu s hodnotou null, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7f3cd-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="7f3cd-110">V předchozím příkladu `where` klauzule odfiltruje všechny elementy null v pořadí kategorií.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="7f3cd-111">Tento postup je nezávislé na hodnotu null. Zkontrolujte v klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="7f3cd-112">Podmíněným výrazem s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?` což je sdružená vlastnost `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f3cd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f3cd-113">Example</span></span>

 <span data-ttu-id="7f3cd-114">V klauzuli join-li jen jeden z klíčů porovnání je typ s možnou hodnotou Null hodnoty, můžete obsadit dalších na typ s možnou hodnotou Null ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="7f3cd-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="7f3cd-115">V následujícím příkladu předpokládáme, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="7f3cd-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7f3cd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f3cd-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="7f3cd-117">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="7f3cd-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="7f3cd-118">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="7f3cd-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
