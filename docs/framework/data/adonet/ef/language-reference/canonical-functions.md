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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="canonical-functions"></a><span data-ttu-id="c120f-102">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-102">Canonical Functions</span></span>
<span data-ttu-id="c120f-103">Tato část popisuje kanonické funkce, které jsou podporovány všechny zprostředkovateli dat a mohou být využívána všechny dotazování technologie.</span><span class="sxs-lookup"><span data-stu-id="c120f-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="c120f-104">Kanonické funkce nelze rozšířit pomocí zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c120f-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="c120f-105">Tyto kanonické funkce bude možné přeložit funkci odpovídající zdroj dat pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c120f-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="c120f-106">To umožňuje volání funkce vyjádřené v běžné formuláře napříč datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="c120f-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="c120f-107">Protože tyto kanonické funkce jsou nezávislé na zdroje dat, jsou definovány argument a návratové typy kanonické funkce z hlediska typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="c120f-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="c120f-108">Některé zdroje dat však nemusí podporovat všechny typy v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="c120f-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="c120f-109">Při použití kanonické funkce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz, příslušnou funkci bude volána ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="c120f-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="c120f-110">Všechny kanonické funkce mít hodnotu null vstup chování a chybové stavy explicitně určena.</span><span class="sxs-lookup"><span data-stu-id="c120f-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="c120f-111">Poskytovatelé úložiště, by měly splňovat chování, ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nevynucuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="c120f-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="c120f-112">Pro scénáře LINQ dotazy proti [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] zahrnují mapování metod modulu CLR do metod v podkladovém zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="c120f-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="c120f-113">Mapa metody CLR na kanonické funkce tak, aby konkrétní nastavena metod bude správně mapovat, bez ohledu na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="c120f-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="c120f-114">Namespace kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="c120f-115">Obor názvů pro kanonické funkce je <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="c120f-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="c120f-116"><xref:System.Data.Metadata.Edm> Obor názvů je automaticky součástí všechny dotazy.</span><span class="sxs-lookup"><span data-stu-id="c120f-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="c120f-117">Ale pokud je importované jiný obor názvů, který obsahuje funkce se stejným názvem jako kanonické funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c120f-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c120f-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c120f-118">In This Section</span></span>  
 [<span data-ttu-id="c120f-119">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="c120f-120">Popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-121">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="c120f-122">Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-123">Řetězcové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="c120f-124">Popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-125">Kanonické funkce pro datum a čas</span><span class="sxs-lookup"><span data-stu-id="c120f-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="c120f-126">Popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-127">Bitové kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="c120f-128">Popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-129">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="c120f-130">Popisuje Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="c120f-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="c120f-131">Jiné kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="c120f-132">Popisuje funkce není klasifikovaný bitové, datum a čas, řetězec, matematické nebo agregace.</span><span class="sxs-lookup"><span data-stu-id="c120f-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c120f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c120f-133">See Also</span></span>  
 [<span data-ttu-id="c120f-134">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c120f-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="c120f-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c120f-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="c120f-136">Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="c120f-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="c120f-137">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="c120f-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
