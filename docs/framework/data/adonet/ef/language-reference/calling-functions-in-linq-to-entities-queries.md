---
title: Volání funkcí v dotazech LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 69a0d11893b528d53dfe5bdca97fa36a65b0a45b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180879"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="add3e-102">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="add3e-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="add3e-103">Témata v této části popisují, jak k volání funkce v jazyce LINQ dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="add3e-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="add3e-104"><xref:System.Data.Objects.EntityFunctions> a <xref:System.Data.Objects.SqlClient.SqlFunctions> třídy poskytují přístup k canonical a funkce databáze jako součást rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="add3e-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="add3e-105">Další informace najdete v tématu [jak: Volání kanonických funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) a [jak: Volání databázových funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="add3e-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="add3e-106">Proces pro volání vlastní funkce vyžaduje tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="add3e-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="add3e-107">Definovat funkci v konceptuálním modelu nebo deklaraci funkce v modelu úložiště.</span><span class="sxs-lookup"><span data-stu-id="add3e-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="add3e-108">Přidejte metodu do vaší aplikace a jejich mapování na funkci v modelu s <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="add3e-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="add3e-109">Volání funkce v technologii LINQ to Entities dotazu.</span><span class="sxs-lookup"><span data-stu-id="add3e-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="add3e-110">Další informace najdete v tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="add3e-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="add3e-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="add3e-111">In This Section</span></span>  
 [<span data-ttu-id="add3e-112">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="add3e-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="add3e-113">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="add3e-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="add3e-114">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="add3e-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="add3e-115">Postupy: Volání modelově definovaných funkcí v dotazech</span><span class="sxs-lookup"><span data-stu-id="add3e-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="add3e-116">Postupy: Volání modelově definovaných funkcí jako objektových metod</span><span class="sxs-lookup"><span data-stu-id="add3e-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="add3e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="add3e-117">See also</span></span>

- [<span data-ttu-id="add3e-118">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="add3e-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [<span data-ttu-id="add3e-119">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="add3e-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [<span data-ttu-id="add3e-120">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="add3e-120">.edmx File Overview</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [<span data-ttu-id="add3e-121">Postupy: Definování vlastních funkcí v konceptuálním modelu</span><span class="sxs-lookup"><span data-stu-id="add3e-121">How to: Define Custom Functions in the Conceptual Model</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
