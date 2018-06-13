---
title: Vytvoření vnořené skupiny
description: Postup vytvoření vnořené skupiny.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273140"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="d4049-103">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="d4049-103">Create a nested group</span></span>

<span data-ttu-id="d4049-104">Následující příklad ukazuje postup vytvoření vnořené skupiny ve výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="d4049-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="d4049-105">Každou skupinu, která je vytvořena podle úrovně rok nebo úrovni student je pak dále rozdělit na skupiny založené na názvy pro osob.</span><span class="sxs-lookup"><span data-stu-id="d4049-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4049-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4049-106">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="d4049-107">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d4049-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="d4049-108">Všimněte si, že tři vnořené `foreach` smyčky jsou nutné k iteraci nad vnitřní prvky vnořené skupiny.</span><span class="sxs-lookup"><span data-stu-id="d4049-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4049-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4049-109">See also</span></span>  
 [<span data-ttu-id="d4049-110">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d4049-110">LINQ Query Expressions</span></span>](index.md)
