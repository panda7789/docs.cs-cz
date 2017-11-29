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
ms.openlocfilehash: ae25f03a091d3a9705a2e445fec948d8c5e15e0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-overview"></a><span data-ttu-id="6aa5f-102">ADO.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="6aa5f-102">ADO.NET Overview</span></span>
<span data-ttu-id="6aa5f-103">ADO.NET zajišťuje konzistentní přístup ke zdrojům dat, jako je například SQL Server a XML a zdroje dat, které jsou k dispozici prostřednictvím technologie OLE DB a rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-103">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="6aa5f-104">Sdílení dat příjemce aplikace můžete použít technologie ADO.NET pro připojení k těmto zdrojům dat a načtení, zpracování a aktualizovat data, která obsahují.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-104">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="6aa5f-105">ADO.NET odděluje přístup k datům z manipulaci s daty do samostatné součásti, které lze použít samostatně nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-105">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="6aa5f-106">ADO.NET obsahuje zprostředkovatele dat .NET Framework pro připojení k databázi, provádění příkazů a načíst výsledky.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-106">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="6aa5f-107">Tyto výsledky se buď zpracovávají přímo, umístit do technologie ADO.NET <xref:System.Data.DataSet> objekt, chcete-li zpřístupnit pro uživatele ad hoc způsobem, společně s daty z více zdrojů nebo předán mezi vrstvami.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-107">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="6aa5f-108">`DataSet` Objekt také lze použít nezávisle na zprostředkovatel dat .NET Framework ke správě dat místní aplikace nebo jako zdroj XML.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-108">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="6aa5f-109">ADO.NET třídy se nacházejí v System.Data.dll a jsou integrované s nalezené v System.Xml.dll třídy XML.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-109">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="6aa5f-110">Ukázkový kód, který se připojuje k databázi, načte data z něj a potom tato data zobrazí v okně konzoly, najdete v části [příklady kódu pro technologii ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="6aa5f-110">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](../../../../docs/framework/data/adonet/ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="6aa5f-111">ADO.NET poskytuje funkce pro vývojáře, kteří vytvářejí spravovaného kódu, které jsou podobné funkce poskytované nativní součást object model (COM) vývojářům pomocí objektů ADO (ActiveX Data).</span><span class="sxs-lookup"><span data-stu-id="6aa5f-111">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="6aa5f-112">Doporučujeme, abyste používali ADO.NET, není ADO pro přístup k datům v aplikacích .NET.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-112">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="6aa5f-113">ADO.NET poskytuje metodě nejvíce přímý přístup k datům v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-113">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="6aa5f-114">Abstrakce vyšší úrovně, který umožňuje aplikacím pracovat v konceptuálním modelu místo základní model úložiště, najdete v článku [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="6aa5f-114">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span></span>  
  
 <span data-ttu-id="6aa5f-115">**Prohlášení o ochraně osobních údajů**: sestavení System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, knihovně System.Data.Linq.dll, System.Data.SqlServerCe.dll a System.Data.DataSetExtensions.dll nepodporují rozlišení mezi uživatele privátní a veřejné daty.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-115">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="6aa5f-116">Tyto sestavení není shromažďování, ukládání nebo přenosu dat privátní všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-116">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="6aa5f-117">Aplikace jiných výrobců mohou však shromažďování, ukládání nebo přenosu privátních dat uživatele pomocí těchto sestavení.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-117">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6aa5f-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6aa5f-118">In This Section</span></span>  
 [<span data-ttu-id="6aa5f-119">Architektura technologie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-119">ADO.NET Architecture</span></span>](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 <span data-ttu-id="6aa5f-120">Poskytuje přehled o architektuře a součástí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-120">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="6aa5f-121">Možnosti technologie ADO.NET a pokyny</span><span class="sxs-lookup"><span data-stu-id="6aa5f-121">ADO.NET Technology Options and Guidelines</span></span>](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="6aa5f-122">Popisuje produkty a technologie, které jsou součástí platformy Data Entity.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-122">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="6aa5f-123">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-123">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 <span data-ttu-id="6aa5f-124">Popisuje, jak je implementované Language-Integrated Query (LINQ) v ADO.NET a poskytuje odkazy na související témata.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-124">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="6aa5f-125">Zprostředkovatelé dat .NET framework</span><span class="sxs-lookup"><span data-stu-id="6aa5f-125">.NET Framework Data Providers</span></span>](../../../../docs/framework/data/adonet/data-providers.md)  
 <span data-ttu-id="6aa5f-126">Obsahuje přehled návrhu zprostředkovatel dat .NET Framework a zprostředkovatele dat rozhraní .NET Framework, které jsou součástí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-126">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="6aa5f-127">Datové sady ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-127">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 <span data-ttu-id="6aa5f-128">Obsahuje přehled `DataSet` návrhu a součásti.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-128">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="6aa5f-129">Spuštění vedle sebe v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-129">Side-by-Side Execution in ADO.NET</span></span>](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 <span data-ttu-id="6aa5f-130">Popisuje rozdíly v ADO.NET verze a jejich vliv na spuštění vedle sebe a kompatibility aplikací.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-130">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="6aa5f-131">Příklady kódu pro technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-131">ADO.NET Code Examples</span></span>](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 <span data-ttu-id="6aa5f-132">Poskytuje ukázek kódu, které načtení dat pomocí zprostředkovatele dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-132">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6aa5f-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6aa5f-133">Related Sections</span></span>  
 [<span data-ttu-id="6aa5f-134">Co je nového v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-134">What's New in ADO.NET</span></span>](../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="6aa5f-135">Nabízí funkce, které jsou v nové [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6aa5f-135">Introduces features that are new in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="6aa5f-136">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-136">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="6aa5f-137">Popisuje postupy pro zabezpečené kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-137">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="6aa5f-138">Mapování datového typu v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-138">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="6aa5f-139">Popisuje mapování datového typu mezi datovými typy rozhraní .NET Framework a zprostředkovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-139">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="6aa5f-140">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="6aa5f-141">Popisuje, jak se připojit ke zdroji dat, načtení dat a upravovat data.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-141">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="6aa5f-142">To zahrnuje `DataReaders` a `DataAdapters`.</span><span class="sxs-lookup"><span data-stu-id="6aa5f-142">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa5f-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="6aa5f-143">See Also</span></span>  
 [<span data-ttu-id="6aa5f-144">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6aa5f-144">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="6aa5f-145">Přístup k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6aa5f-145">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [<span data-ttu-id="6aa5f-146">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="6aa5f-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
