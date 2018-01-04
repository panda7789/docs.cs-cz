---
title: "ADO.NET – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e18115e460bf546c2fd6263e4671457a3da68f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-overview"></a><span data-ttu-id="331e4-102">ADO.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="331e4-102">ADO.NET Overview</span></span>
<span data-ttu-id="331e4-103">ADO.NET zajišťuje konzistentní přístup ke zdrojům dat, jako je například SQL Server a XML a zdroje dat, které jsou k dispozici prostřednictvím technologie OLE DB a rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="331e4-103">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="331e4-104">Sdílení dat příjemce aplikace můžete použít technologie ADO.NET pro připojení k těmto zdrojům dat a načtení, zpracování a aktualizovat data, která obsahují.</span><span class="sxs-lookup"><span data-stu-id="331e4-104">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="331e4-105">ADO.NET odděluje přístup k datům z manipulaci s daty do samostatné součásti, které lze použít samostatně nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="331e4-105">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="331e4-106">ADO.NET obsahuje zprostředkovatele dat .NET Framework pro připojení k databázi, provádění příkazů a načíst výsledky.</span><span class="sxs-lookup"><span data-stu-id="331e4-106">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="331e4-107">Tyto výsledky se buď zpracovávají přímo, umístit do technologie ADO.NET <xref:System.Data.DataSet> objekt, chcete-li zpřístupnit pro uživatele ad hoc způsobem, společně s daty z více zdrojů nebo předán mezi vrstvami.</span><span class="sxs-lookup"><span data-stu-id="331e4-107">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="331e4-108">`DataSet` Objekt také lze použít nezávisle na zprostředkovatel dat .NET Framework ke správě dat místní aplikace nebo jako zdroj XML.</span><span class="sxs-lookup"><span data-stu-id="331e4-108">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="331e4-109">ADO.NET třídy se nacházejí v System.Data.dll a jsou integrované s nalezené v System.Xml.dll třídy XML.</span><span class="sxs-lookup"><span data-stu-id="331e4-109">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="331e4-110">Ukázkový kód, který se připojuje k databázi, načte data z něj a potom tato data zobrazí v okně konzoly, najdete v části [příklady kódu pro technologii ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="331e4-110">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="331e4-111">ADO.NET poskytuje funkce pro vývojáře, kteří vytvářejí spravovaného kódu, které jsou podobné funkce poskytované nativní součást object model (COM) vývojářům pomocí objektů ADO (ActiveX Data).</span><span class="sxs-lookup"><span data-stu-id="331e4-111">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="331e4-112">Doporučujeme, abyste používali ADO.NET, není ADO pro přístup k datům v aplikacích .NET.</span><span class="sxs-lookup"><span data-stu-id="331e4-112">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="331e4-113">ADO.NET poskytuje metodě nejvíce přímý přístup k datům v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="331e4-113">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="331e4-114">Abstrakce vyšší úrovně, který umožňuje aplikacím pracovat v konceptuálním modelu místo základní model úložiště, najdete v článku [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="331e4-114">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span></span>  
  
 <span data-ttu-id="331e4-115">**Prohlášení o ochraně osobních údajů**: sestavení System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, knihovně System.Data.Linq.dll, System.Data.SqlServerCe.dll a System.Data.DataSetExtensions.dll nepodporují rozlišení mezi uživatele privátní a veřejné daty.</span><span class="sxs-lookup"><span data-stu-id="331e4-115">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="331e4-116">Tyto sestavení není shromažďování, ukládání nebo přenosu dat privátní všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="331e4-116">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="331e4-117">Aplikace jiných výrobců mohou však shromažďování, ukládání nebo přenosu privátních dat uživatele pomocí těchto sestavení.</span><span class="sxs-lookup"><span data-stu-id="331e4-117">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="331e4-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="331e4-118">In This Section</span></span>  
 [<span data-ttu-id="331e4-119">Architektura ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-119">ADO.NET Architecture</span></span>](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 <span data-ttu-id="331e4-120">Poskytuje přehled o architektuře a součástí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="331e4-120">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="331e4-121">Možnosti a pokyny pro ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-121">ADO.NET Technology Options and Guidelines</span></span>](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="331e4-122">Popisuje produkty a technologie, které jsou součástí platformy Data Entity.</span><span class="sxs-lookup"><span data-stu-id="331e4-122">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="331e4-123">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-123">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 <span data-ttu-id="331e4-124">Popisuje, jak je implementované Language-Integrated Query (LINQ) v ADO.NET a poskytuje odkazy na související témata.</span><span class="sxs-lookup"><span data-stu-id="331e4-124">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="331e4-125">Zprostředkovatelé dat .NET Framework</span><span class="sxs-lookup"><span data-stu-id="331e4-125">.NET Framework Data Providers</span></span>](../../../../docs/framework/data/adonet/data-providers.md)  
 <span data-ttu-id="331e4-126">Obsahuje přehled návrhu zprostředkovatel dat .NET Framework a zprostředkovatele dat rozhraní .NET Framework, které jsou součástí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="331e4-126">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="331e4-127">Datové sady ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-127">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 <span data-ttu-id="331e4-128">Obsahuje přehled `DataSet` návrhu a součásti.</span><span class="sxs-lookup"><span data-stu-id="331e4-128">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="331e4-129">Souběžné spouštění v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-129">Side-by-Side Execution in ADO.NET</span></span>](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 <span data-ttu-id="331e4-130">Popisuje rozdíly v ADO.NET verze a jejich vliv na spuštění vedle sebe a kompatibility aplikací.</span><span class="sxs-lookup"><span data-stu-id="331e4-130">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="331e4-131">Příklady kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-131">ADO.NET Code Examples</span></span>](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 <span data-ttu-id="331e4-132">Poskytuje ukázek kódu, které načtení dat pomocí zprostředkovatele dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="331e4-132">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="331e4-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="331e4-133">Related Sections</span></span>  
 [<span data-ttu-id="331e4-134">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-134">What's New in ADO.NET</span></span>](../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="331e4-135">Nabízí funkce, které jsou v nové [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="331e4-135">Introduces features that are new in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="331e4-136">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-136">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="331e4-137">Popisuje postupy pro zabezpečené kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="331e4-137">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="331e4-138">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-138">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="331e4-139">Popisuje mapování datového typu mezi datovými typy rozhraní .NET Framework a zprostředkovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="331e4-139">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="331e4-140">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="331e4-141">Popisuje, jak se připojit ke zdroji dat, načtení dat a upravovat data.</span><span class="sxs-lookup"><span data-stu-id="331e4-141">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="331e4-142">To zahrnuje `DataReaders` a `DataAdapters`.</span><span class="sxs-lookup"><span data-stu-id="331e4-142">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331e4-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="331e4-143">See Also</span></span>  
 [<span data-ttu-id="331e4-144">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="331e4-144">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="331e4-145">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="331e4-145">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [<span data-ttu-id="331e4-146">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="331e4-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
