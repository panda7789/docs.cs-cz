---
title: Volání funkcí v dotazech LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251266"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="120ae-102">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="120ae-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="120ae-103">Témata v této části popisují, jak volat funkce v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="120ae-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="120ae-104">Třídy <xref:System.Data.Objects.EntityFunctions> a<xref:System.Data.Objects.SqlClient.SqlFunctions> poskytují přístup k kanonickým a databázovým funkcím jako součást Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="120ae-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="120ae-105">Další informace najdete v tématu [jak: Zavolejte kanonické](how-to-call-canonical-functions.md) funkce [a postupy: Volání funkcí](how-to-call-database-functions.md)databáze.</span><span class="sxs-lookup"><span data-stu-id="120ae-105">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="120ae-106">Proces volání vlastní funkce vyžaduje tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="120ae-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="120ae-107">Definujte funkci ve koncepčním modelu nebo Deklarujte funkci v modelu úložiště.</span><span class="sxs-lookup"><span data-stu-id="120ae-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="120ae-108">Přidejte do své aplikace metodu a namapujte ji na funkci v modelu pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="120ae-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="120ae-109">Volání funkce v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="120ae-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="120ae-110">Další informace najdete v tématech v této části.</span><span class="sxs-lookup"><span data-stu-id="120ae-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="120ae-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="120ae-111">In This Section</span></span>  
 [<span data-ttu-id="120ae-112">Postupy: Volání normativních funkcí</span><span class="sxs-lookup"><span data-stu-id="120ae-112">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="120ae-113">Postupy: Volání funkcí databáze</span><span class="sxs-lookup"><span data-stu-id="120ae-113">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="120ae-114">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="120ae-114">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="120ae-115">Postupy: Volání funkcí definovaných modelem v dotazech</span><span class="sxs-lookup"><span data-stu-id="120ae-115">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="120ae-116">Postupy: Volání funkcí definovaných modelem jako metod objektů</span><span class="sxs-lookup"><span data-stu-id="120ae-116">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="120ae-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="120ae-117">See also</span></span>

- [<span data-ttu-id="120ae-118">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="120ae-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="120ae-119">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="120ae-119">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="120ae-120">[Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="120ae-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="120ae-121">[Postupy: Definování vlastních funkcí v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="120ae-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
