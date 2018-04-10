---
title: Technologie LINQ to SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 62f7a3b0fcefa9eb6f5b56d96217a9988a193104
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="linq-to-sql"></a><span data-ttu-id="e9a47-102">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e9a47-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e9a47-103">je součástí [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] verze 3.5, který poskytuje běhové infrastrukturu pro správu relačních dat jako objekty.</span><span class="sxs-lookup"><span data-stu-id="e9a47-103"> is a component of [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9a47-104">Relační data se zobrazí jako kolekce dvourozměrná tabulek (*vztahů* nebo *ploché soubory*), kde společné sloupce tabulky vzájemně souvisejí.</span><span class="sxs-lookup"><span data-stu-id="e9a47-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="e9a47-105">Chcete-li použít [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektivně, musí mít některé znalost základní principy relačních databází.</span><span class="sxs-lookup"><span data-stu-id="e9a47-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="e9a47-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], datový model relační databáze je namapována na objektový model vyjádřené v programovací jazyk vývojář.</span><span class="sxs-lookup"><span data-stu-id="e9a47-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="e9a47-107">Když je aplikace spuštěná, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy language-integrated ve model objektu do SQL a odešle je do databáze pro provedení.</span><span class="sxs-lookup"><span data-stu-id="e9a47-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="e9a47-108">Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží je zpět na objekty, které můžete pracovat v programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="e9a47-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="e9a47-109">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] se obvykle používají [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], který poskytuje uživatelské rozhraní pro implementaci řadu funkcí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a47-109">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="e9a47-110">Dokumentace, která je součástí této verze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] popisuje základní stavební bloky, procesy a postupy potřebné pro vytvoření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9a47-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="e9a47-111">Můžete také prohledat Microsoft Docs pro specifické problémy a se můžete zapojit [LINQ fórum](http://go.microsoft.com/fwlink/?LinkId=76488), kde můžete složitější témata podrobně popisují s odborníky.</span><span class="sxs-lookup"><span data-stu-id="e9a47-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="e9a47-112">Nakonec [technologie LINQ to SQL: .NET Language-Integrated dotaz na relační Data](http://go.microsoft.com/fwlink/?LinkId=93205) dokumentu white paper podrobnosti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie kompletní s [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] a příklady kódu pro C#.</span><span class="sxs-lookup"><span data-stu-id="e9a47-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9a47-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e9a47-113">In This Section</span></span>  
 [<span data-ttu-id="e9a47-114">Začínáme</span><span class="sxs-lookup"><span data-stu-id="e9a47-114">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 <span data-ttu-id="e9a47-115">Obsahuje přehled zhuštěné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] společně s informacemi o tom, jak začít používat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a47-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="e9a47-116">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="e9a47-116">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="e9a47-117">Popisuje kroky pro mapování, dotazování, aktualizaci, ladění a podobných úloh.</span><span class="sxs-lookup"><span data-stu-id="e9a47-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="e9a47-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="e9a47-118">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 <span data-ttu-id="e9a47-119">Poskytuje referenční informace o několik aspektů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a47-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e9a47-120">Témata zahrnují mapování typu SQL CLR, operátor překlad dotazu na standardní a další.</span><span class="sxs-lookup"><span data-stu-id="e9a47-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="e9a47-121">Ukázky</span><span class="sxs-lookup"><span data-stu-id="e9a47-121">Samples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 <span data-ttu-id="e9a47-122">Obsahuje odkazy na [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] a C# – ukázky.</span><span class="sxs-lookup"><span data-stu-id="e9a47-122">Provides links to [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9a47-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e9a47-123">Related Sections</span></span>  
 [<span data-ttu-id="e9a47-124">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e9a47-124">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="e9a47-125">Obsahuje přehled [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie.</span><span class="sxs-lookup"><span data-stu-id="e9a47-125">Provides an overview of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies.</span></span>  
  
 [<span data-ttu-id="e9a47-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="e9a47-126">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="e9a47-127">Popisuje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] uživatele.</span><span class="sxs-lookup"><span data-stu-id="e9a47-127">Describes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies for [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] users.</span></span>  
  
 [<span data-ttu-id="e9a47-128">Technologie LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e9a47-128">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 <span data-ttu-id="e9a47-129">Obsahuje odkazy na [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portálu.</span><span class="sxs-lookup"><span data-stu-id="e9a47-129">Links to the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span></span>  
  
 [<span data-ttu-id="e9a47-130">Technologie LINQ to SQL návody</span><span class="sxs-lookup"><span data-stu-id="e9a47-130">LINQ to SQL Walkthroughs</span></span>](http://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 <span data-ttu-id="e9a47-131">Uvádí postupy, které jsou k dispozici pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a47-131">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="e9a47-132">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="e9a47-132">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 <span data-ttu-id="e9a47-133">Popisuje, jak stáhnout ukázkové databáze používají v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="e9a47-133">Describes how to download sample databases used in the documentation.</span></span>  
  
 [<span data-ttu-id="e9a47-134">Přehled technologie LinqDataSource</span><span class="sxs-lookup"><span data-stu-id="e9a47-134">LinqDataSource Technology Overview</span></span>](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <span data-ttu-id="e9a47-135">Popisuje, jak <xref:System.Web.UI.WebControls.LinqDataSource> řízení zpřístupňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] na vývojáři webů prostřednictvím [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektury datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="e9a47-135">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] to Web developers through the [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] data-source control architecture.</span></span>
