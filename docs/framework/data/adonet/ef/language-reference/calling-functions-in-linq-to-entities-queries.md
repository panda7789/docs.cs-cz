---
title: Volání funkcí v dotazech LINQ to Entities
description: Pomocí těchto článků zjistíte, jak třídy EntityFunctions a SqlFunctions poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286854"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="9afe5-103">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9afe5-103">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="9afe5-104">Témata v této části popisují, jak volat funkce v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="9afe5-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="9afe5-105"><xref:System.Data.Objects.EntityFunctions>Třídy a <xref:System.Data.Objects.SqlClient.SqlFunctions> poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9afe5-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="9afe5-106">Další informace naleznete v tématu [How to: Calling Kanonick Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9afe5-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="9afe5-107">Proces volání vlastní funkce vyžaduje tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="9afe5-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="9afe5-108">Definujte funkci ve koncepčním modelu nebo Deklarujte funkci v modelu úložiště.</span><span class="sxs-lookup"><span data-stu-id="9afe5-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="9afe5-109">Přidejte do své aplikace metodu a namapujte ji na funkci v modelu pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9afe5-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="9afe5-110">Volání funkce v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9afe5-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="9afe5-111">Další informace najdete v tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="9afe5-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9afe5-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9afe5-112">In This Section</span></span>  
 [<span data-ttu-id="9afe5-113">Postupy: Volání kanonických funkcí</span><span class="sxs-lookup"><span data-stu-id="9afe5-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="9afe5-114">Postupy: Volání databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="9afe5-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="9afe5-115">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="9afe5-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="9afe5-116">Postupy: Volání modelově definovaných funkcí v dotazech</span><span class="sxs-lookup"><span data-stu-id="9afe5-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="9afe5-117">Postupy: Volání modelově definovaných funkcí jako objektových metod</span><span class="sxs-lookup"><span data-stu-id="9afe5-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="9afe5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9afe5-118">See also</span></span>

- [<span data-ttu-id="9afe5-119">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9afe5-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="9afe5-120">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="9afe5-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="9afe5-121">[Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9afe5-121">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="9afe5-122">[Postupy: definování vlastních funkcí v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9afe5-122">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
