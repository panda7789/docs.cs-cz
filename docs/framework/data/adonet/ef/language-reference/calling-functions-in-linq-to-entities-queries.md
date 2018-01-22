---
title: "Volání funkcí v technologii LINQ to Entities dotazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7199c41f8bcf81340956b17f616bec76e534dcc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="0738d-102">Volání funkcí v technologii LINQ to Entities dotazy</span><span class="sxs-lookup"><span data-stu-id="0738d-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="0738d-103">Témata v této části popisují, jak volat funkce v technologii LINQ dotazy entity.</span><span class="sxs-lookup"><span data-stu-id="0738d-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="0738d-104"><xref:System.Data.Objects.EntityFunctions> a <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy poskytují přístup k kanonické a funkce databáze v rámci rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0738d-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="0738d-105">Další informace najdete v tématu [postupy: volání kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) a [postupy: volání funkce databáze](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0738d-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="0738d-106">Proces pro volání vlastní funkce vyžaduje tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="0738d-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="0738d-107">Definice funkce v konceptuálním modelu nebo deklarovat funkce v modelu úložiště.</span><span class="sxs-lookup"><span data-stu-id="0738d-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="0738d-108">Přidání metody do vaší aplikace a namapovat je funkce v modelu s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0738d-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="0738d-109">Volání funkce v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0738d-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="0738d-110">Další informace najdete v tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="0738d-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0738d-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0738d-111">In This Section</span></span>  
 [<span data-ttu-id="0738d-112">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="0738d-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="0738d-113">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="0738d-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="0738d-114">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="0738d-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="0738d-115">Postupy: Volání modelově definovaných funkcí v dotazech</span><span class="sxs-lookup"><span data-stu-id="0738d-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="0738d-116">Postupy: Volání modelově definovaných funkcí jako objektových metod</span><span class="sxs-lookup"><span data-stu-id="0738d-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="0738d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0738d-117">See Also</span></span>  
 [<span data-ttu-id="0738d-118">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0738d-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="0738d-119">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="0738d-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="0738d-120">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="0738d-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="0738d-121">Postupy: definování vlastní funkce v konceptuálním modelu</span><span class="sxs-lookup"><span data-stu-id="0738d-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
