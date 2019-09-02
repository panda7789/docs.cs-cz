---
title: Datové sady, datové tabulky a datová zobrazení
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4b5e81f415685d6ee3529c7e4f9d389e8017427e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203632"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="2a4c8-102">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="2a4c8-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="2a4c8-103">ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="2a4c8-104"><xref:System.Data.DataSet> Představuje kompletní sadu dat, včetně tabulek, které obsahují, vyřazení a omezení dat a také vztahů mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="2a4c8-105">Existuje několik způsobů práce s a <xref:System.Data.DataSet>, které lze použít nezávisle nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="2a4c8-106">Můžete:</span><span class="sxs-lookup"><span data-stu-id="2a4c8-106">You can:</span></span>  
  
- <span data-ttu-id="2a4c8-107">Programové vytvoření <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>a v rámci<xref:System.Data.DataSet> a naplnění tabulek daty. <xref:System.Data.Constraint></span><span class="sxs-lookup"><span data-stu-id="2a4c8-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="2a4c8-108">Naplňte tabulky daty z existujícího relačního zdroje dat `DataAdapter`pomocí. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="2a4c8-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="2a4c8-109">Načtěte a zachovejte <xref:System.Data.DataSet> obsah pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="2a4c8-110">Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2a4c8-110">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2a4c8-111">Silné typy <xref:System.Data.DataSet> lze také přenést pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="2a4c8-112">Návrh je <xref:System.Data.DataSet> ideální pro přenos dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="2a4c8-113">Přehled webových služeb XML najdete v tématu [Přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2a4c8-113">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="2a4c8-114">Příklad použití <xref:System.Data.DataSet> webové služby XML naleznete v tématu [spotřebovávání datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="2a4c8-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a4c8-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2a4c8-115">In This Section</span></span>  
 [<span data-ttu-id="2a4c8-116">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-116">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="2a4c8-117">Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2a4c8-118">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-118">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="2a4c8-119">Popisuje, jak vytvořit a přidat tabulky a sloupce do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2a4c8-120">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="2a4c8-120">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="2a4c8-121">Popisuje, jak vytvořit relace mezi tabulkami v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2a4c8-122">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="2a4c8-122">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="2a4c8-123">Popisuje, jak použít relace mezi tabulkami v <xref:System.Data.DataSet> k vrácení podřízených nebo nadřazených řádků relace typu nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="2a4c8-124">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-124">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="2a4c8-125">Popisuje, jak sloučit obsah <xref:System.Data.DataSet>jednoho, <xref:System.Data.DataTable>nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2a4c8-126">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-126">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="2a4c8-127">Popisuje <xref:System.Data.DataSet> , jak vytvořit kopii, která může obsahovat schéma i zadaná data.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="2a4c8-128">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-128">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="2a4c8-129">Popisuje události <xref:System.Data.DataSet> a, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="2a4c8-130">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-130">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="2a4c8-131">Popisuje, co je <xref:System.Data.DataSet> typu a jak ho vytvořit a použít.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="2a4c8-132">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2a4c8-132">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="2a4c8-133">Popisuje <xref:System.Data.DataTable>, jak vytvořit, definovat schéma a manipulovat s daty.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="2a4c8-134">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="2a4c8-134">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="2a4c8-135">Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="2a4c8-136">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="2a4c8-136">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="2a4c8-137">Popisuje, jak vytvořit a pracovat `DataViews` s <xref:System.Data.DataView> událostmi a pracovat s nimi.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="2a4c8-138">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="2a4c8-138">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="2a4c8-139">Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a uchování obsahu <xref:System.Data.DataSet> jako XML data.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="2a4c8-140">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="2a4c8-140">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="2a4c8-141">Popisuje, jak vytvořit webovou službu XML, která používá <xref:System.Data.DataSet> k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a4c8-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2a4c8-142">Related Sections</span></span>  
 [<span data-ttu-id="2a4c8-143">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a4c8-143">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="2a4c8-144">Přináší nové funkce, které jsou v ADO.NET novinkou.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="2a4c8-145">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a4c8-145">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="2a4c8-146">Poskytuje Úvod k návrhu a součástem ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="2a4c8-147">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="2a4c8-147">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="2a4c8-148">Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="2a4c8-149">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="2a4c8-149">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="2a4c8-150">Popisuje, jak vyřešit změny dat v datové **sadě** zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="2a4c8-151">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="2a4c8-151">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="2a4c8-152">Popisuje, jak naplnit **datovou sadu** pomocí informací o primárním klíči ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2a4c8-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4c8-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a4c8-153">See also</span></span>

- [<span data-ttu-id="2a4c8-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a4c8-154">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="2a4c8-155">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2a4c8-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
