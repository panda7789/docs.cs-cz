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
ms.openlocfilehash: b80eeedc67678d703664eb705408a72b7e4a2274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="canonical-functions"></a><span data-ttu-id="98951-102">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="98951-102">Canonical Functions</span></span>
<span data-ttu-id="98951-103">Tato část popisuje kanonické funkce, které jsou podporovány všechny zprostředkovateli dat a mohou být využívána všechny dotazování technologie.</span><span class="sxs-lookup"><span data-stu-id="98951-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="98951-104">Kanonické funkce nelze rozšířit pomocí zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="98951-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="98951-105">Tyto kanonické funkce bude možné přeložit funkci odpovídající zdroj dat pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="98951-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="98951-106">To umožňuje volání funkce vyjádřené v běžné formuláře napříč datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="98951-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="98951-107">Protože tyto kanonické funkce jsou nezávislé na zdroje dat, jsou definovány argument a návratové typy kanonické funkce z hlediska typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="98951-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="98951-108">Některé zdroje dat však nemusí podporovat všechny typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="98951-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="98951-109">Při použití kanonické funkce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz, příslušnou funkci bude volána ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="98951-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="98951-110">Všechny kanonické funkce mít hodnotu null vstup chování a chybové stavy explicitně určena.</span><span class="sxs-lookup"><span data-stu-id="98951-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="98951-111">Poskytovatelé úložiště, by měly splňovat chování, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nevynucuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="98951-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="98951-112">Pro scénáře LINQ dotazy proti [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] zahrnují mapování metod modulu CLR do metod v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="98951-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="98951-113">Mapa metody CLR na kanonické funkce tak, aby konkrétní nastavena metod bude správně mapovat, bez ohledu na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="98951-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="98951-114">Namespace kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="98951-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="98951-115">Obor názvů pro kanonické funkce je <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="98951-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="98951-116"><xref:System.Data.Metadata.Edm> Obor názvů je automaticky součástí všechny dotazy.</span><span class="sxs-lookup"><span data-stu-id="98951-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="98951-117">Ale pokud je importované jiný obor názvů, který obsahuje funkce se stejným názvem jako kanonické funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="98951-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98951-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="98951-118">In This Section</span></span>  
 [<span data-ttu-id="98951-119">Kanonické agregační funkce</span><span class="sxs-lookup"><span data-stu-id="98951-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="98951-120">Popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-121">Matematické funkce kanonickém tvaru</span><span class="sxs-lookup"><span data-stu-id="98951-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="98951-122">Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-123">Kanonické funkce řetězce</span><span class="sxs-lookup"><span data-stu-id="98951-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="98951-124">Popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-125">Kanonické funkce data a času</span><span class="sxs-lookup"><span data-stu-id="98951-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="98951-126">Popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-127">Bitový kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="98951-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="98951-128">Popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-129">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="98951-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="98951-130">Popisuje Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="98951-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="98951-131">Další kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="98951-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="98951-132">Popisuje funkce není klasifikovaný bitové, datum a čas, řetězec, matematické nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="98951-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98951-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="98951-133">See Also</span></span>  
 [<span data-ttu-id="98951-134">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="98951-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="98951-135">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="98951-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="98951-136">Konceptuální Model kanonický k mapování funkcí SQL serveru</span><span class="sxs-lookup"><span data-stu-id="98951-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="98951-137">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="98951-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
