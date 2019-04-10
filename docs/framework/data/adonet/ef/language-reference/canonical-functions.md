---
title: Kanonické funkce
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 380c1dbcf86d8bbb844c2b226697d72d00c3e81a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202934"
---
# <a name="canonical-functions"></a><span data-ttu-id="5496f-102">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-102">Canonical Functions</span></span>
<span data-ttu-id="5496f-103">Tato část popisuje kanonické funkce, které jsou podporovány všechny poskytovatele dat a může využívat všechny dotazy technologie.</span><span class="sxs-lookup"><span data-stu-id="5496f-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="5496f-104">Kanonické funkce nelze rozšířit poskytovatelem.</span><span class="sxs-lookup"><span data-stu-id="5496f-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="5496f-105">Tyto kanonické funkce se přeložit na funkci odpovídající zdroj dat poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="5496f-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="5496f-106">To umožňuje vyjádřené v běžné formě napříč zdroji dat obsahující záznamy volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="5496f-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="5496f-107">Protože tyto kanonické funkce jsou nezávislé na zdroje dat, jsou definována v argumentu a návratovým typem kanonické funkce typů v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="5496f-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="5496f-108">Některé zdroje dat však nemusí podporovat všechny typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="5496f-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="5496f-109">Při použití kanonické funkce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu, příslušnou funkci bude volána ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5496f-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="5496f-110">Všechny kanonické funkce mají chování vstupní hodnotu null a chybové stavy explicitně zadán.</span><span class="sxs-lookup"><span data-stu-id="5496f-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="5496f-111">Poskytovatelé Store by měly splňovat toto chování ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nevynucuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="5496f-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="5496f-112">U scénářů s LINQ dotazy proti [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] zahrnují mapování metod v podkladovém zdroji dat metod modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5496f-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="5496f-113">Mapu metod modulu CLR, aby kanonické funkce tak, aby konkrétní sadu metod se správně rozvržení, bez ohledu na zdroj dat</span><span class="sxs-lookup"><span data-stu-id="5496f-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="5496f-114">Namespace kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="5496f-115">Obor názvů pro kanonické funkce je <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="5496f-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="5496f-116"><xref:System.Data.Metadata.Edm> Obor názvů je automaticky zahrnut ve všech dotazů.</span><span class="sxs-lookup"><span data-stu-id="5496f-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="5496f-117">Ale pokud dojde k importu jiný obor názvů, který obsahuje funkce se stejným názvem jako kanonické funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5496f-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5496f-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5496f-118">In This Section</span></span>  
 [<span data-ttu-id="5496f-119">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="5496f-120">Tento článek popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-121">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="5496f-122">Tento článek popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-123">Řetězcové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="5496f-124">Tento článek popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-125">Kanonické funkce pro datum a čas</span><span class="sxs-lookup"><span data-stu-id="5496f-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="5496f-126">Tento článek popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-127">Bitové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="5496f-128">Tento článek popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-129">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="5496f-130">Tento článek popisuje Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5496f-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="5496f-131">Jiné kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="5496f-132">Tento článek popisuje funkce nejsou klasifikovány jako bitové operace, datum a čas, řetězec, matematických výpočtů nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="5496f-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5496f-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5496f-133">See also</span></span>

- [<span data-ttu-id="5496f-134">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5496f-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="5496f-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5496f-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="5496f-136">Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5496f-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="5496f-137">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="5496f-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
