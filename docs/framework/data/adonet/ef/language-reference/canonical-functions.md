---
title: "Kanonické funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: da48efc110669c170fc409e22cb8402f471b22e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="canonical-functions"></a><span data-ttu-id="311ca-102">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-102">Canonical Functions</span></span>
<span data-ttu-id="311ca-103">Tato část popisuje kanonické funkce, které jsou podporovány všechny zprostředkovateli dat a mohou být využívána všechny dotazování technologie.</span><span class="sxs-lookup"><span data-stu-id="311ca-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="311ca-104">Kanonické funkce nelze rozšířit pomocí zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="311ca-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="311ca-105">Tyto kanonické funkce bude možné přeložit funkci odpovídající zdroj dat pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="311ca-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="311ca-106">To umožňuje volání funkce vyjádřené v běžné formuláře napříč datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="311ca-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="311ca-107">Protože tyto kanonické funkce jsou nezávislé na zdroje dat, jsou definovány argument a návratové typy kanonické funkce z hlediska typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="311ca-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="311ca-108">Některé zdroje dat však nemusí podporovat všechny typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="311ca-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="311ca-109">Při použití kanonické funkce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz, příslušnou funkci bude volána ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="311ca-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="311ca-110">Všechny kanonické funkce mít hodnotu null vstup chování a chybové stavy explicitně určena.</span><span class="sxs-lookup"><span data-stu-id="311ca-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="311ca-111">Poskytovatelé úložiště, by měly splňovat chování, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nevynucuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="311ca-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="311ca-112">Pro scénáře LINQ dotazy proti [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] zahrnují mapování metod modulu CLR do metod v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="311ca-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="311ca-113">Mapa metody CLR na kanonické funkce tak, aby konkrétní nastavena metod bude správně mapovat, bez ohledu na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="311ca-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="311ca-114">Namespace kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="311ca-115">Obor názvů pro kanonické funkce je <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="311ca-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="311ca-116"><xref:System.Data.Metadata.Edm> Obor názvů je automaticky součástí všechny dotazy.</span><span class="sxs-lookup"><span data-stu-id="311ca-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="311ca-117">Ale pokud je importované jiný obor názvů, který obsahuje funkce se stejným názvem jako kanonické funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="311ca-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="311ca-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="311ca-118">In This Section</span></span>  
 [<span data-ttu-id="311ca-119">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="311ca-120">Popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-121">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="311ca-122">Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-123">Řetězcové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="311ca-124">Popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-125">Kanonické funkce pro datum a čas</span><span class="sxs-lookup"><span data-stu-id="311ca-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="311ca-126">Popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-127">Bitové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="311ca-128">Popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-129">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="311ca-130">Popisuje Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="311ca-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="311ca-131">Jiné kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="311ca-132">Popisuje funkce není klasifikovaný bitové, datum a čas, řetězec, matematické nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="311ca-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311ca-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="311ca-133">See Also</span></span>  
 [<span data-ttu-id="311ca-134">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="311ca-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="311ca-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="311ca-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="311ca-136">Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="311ca-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="311ca-137">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="311ca-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
