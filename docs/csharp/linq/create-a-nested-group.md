---
title: "Vytvoření vnořené skupiny"
description: "Postup vytvoření vnořené skupiny."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="162f9-104">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="162f9-104">Create a nested group</span></span>

<span data-ttu-id="162f9-105">Následující příklad ukazuje postup vytvoření vnořené skupiny ve výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="162f9-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="162f9-106">Každou skupinu, která je vytvořena podle úrovně rok nebo úrovni student je pak dále rozdělit na skupiny založené na názvy pro osob.</span><span class="sxs-lookup"><span data-stu-id="162f9-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="162f9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="162f9-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="162f9-108">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="162f9-109">Všimněte si, že tři vnořené `foreach` smyčky jsou nutné k iteraci nad vnitřní prvky vnořené skupiny.</span><span class="sxs-lookup"><span data-stu-id="162f9-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162f9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="162f9-110">See also</span></span>  
 [<span data-ttu-id="162f9-111">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="162f9-111">LINQ Query Expressions</span></span>](index.md)
