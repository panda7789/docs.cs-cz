---
title: Volání funkcí v dotazech LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 4aed9fd59cceb72baac9dc12a85c52787c4b3866
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506941"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="028b5-102">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="028b5-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="028b5-103">Témata v této části popisují, jak k volání funkce v jazyce LINQ dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="028b5-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="028b5-104"><xref:System.Data.Objects.EntityFunctions> a <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy poskytují přístup k canonical a funkce databáze jako součást rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="028b5-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="028b5-105">Další informace najdete v tématu [postupy: volání kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) a [postupy: volání databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="028b5-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="028b5-106">Proces pro volání vlastní funkce vyžaduje tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="028b5-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="028b5-107">Definovat funkci v konceptuálním modelu nebo deklaraci funkce v modelu úložiště.</span><span class="sxs-lookup"><span data-stu-id="028b5-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="028b5-108">Přidejte metodu do vaší aplikace a jejich mapování na funkci v modelu s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="028b5-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="028b5-109">Volání funkce v technologii LINQ to Entities dotazu.</span><span class="sxs-lookup"><span data-stu-id="028b5-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="028b5-110">Další informace najdete v tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="028b5-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="028b5-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="028b5-111">In This Section</span></span>  
 [<span data-ttu-id="028b5-112">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="028b5-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="028b5-113">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="028b5-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="028b5-114">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="028b5-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="028b5-115">Postupy: Volání modelově definovaných funkcí v dotazech</span><span class="sxs-lookup"><span data-stu-id="028b5-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="028b5-116">Postupy: Volání modelově definovaných funkcí jako objektových metod</span><span class="sxs-lookup"><span data-stu-id="028b5-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="028b5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="028b5-117">See Also</span></span>  
 [<span data-ttu-id="028b5-118">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="028b5-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="028b5-119">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="028b5-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="028b5-120">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="028b5-120">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="028b5-121">Postupy: definování vlastních funkcí v konceptuálním modelu</span><span class="sxs-lookup"><span data-stu-id="028b5-121">How to: Define Custom Functions in the Conceptual Model</span></span>](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
