---
title: Datové sady, datové tabulky a datová zobrazení
description: Seznamte se s různými způsoby, jak pracovat s datovou sadou ADO.NET, což je reprezentace dat rezidentních v paměti, která poskytuje konzistentní relační programovací model.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286893"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="4a12b-103">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="4a12b-103">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="4a12b-104">ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="4a12b-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="4a12b-105"><xref:System.Data.DataSet>Představuje kompletní sadu dat, včetně tabulek, které obsahují, vyřazení a omezení dat a také vztahů mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="4a12b-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="4a12b-106">Existuje několik způsobů práce s a <xref:System.Data.DataSet> , které lze použít nezávisle nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="4a12b-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="4a12b-107">Další možnosti:</span><span class="sxs-lookup"><span data-stu-id="4a12b-107">You can:</span></span>  
  
- <span data-ttu-id="4a12b-108">Programové vytvoření <xref:System.Data.DataTable> , a <xref:System.Data.DataRelation> <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulek daty.</span><span class="sxs-lookup"><span data-stu-id="4a12b-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="4a12b-109">Naplňte <xref:System.Data.DataSet> tabulky daty z existujícího relačního zdroje dat pomocí `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="4a12b-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="4a12b-110">Načtěte a zachovejte <xref:System.Data.DataSet> obsah pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="4a12b-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="4a12b-111">Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="4a12b-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4a12b-112">Silné typy <xref:System.Data.DataSet> lze také přenést pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="4a12b-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="4a12b-113">Návrh je <xref:System.Data.DataSet> ideální pro přenos dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="4a12b-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="4a12b-114">Přehled webových služeb XML najdete v tématu [Přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4a12b-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="4a12b-115">Příklad použití <xref:System.Data.DataSet> webové služby XML naleznete v tématu [spotřebovávání datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="4a12b-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a12b-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4a12b-116">In This Section</span></span>  
 [<span data-ttu-id="4a12b-117">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-117">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="4a12b-118">Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-118">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a12b-119">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-119">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="4a12b-120">Popisuje, jak vytvořit a přidat tabulky a sloupce do <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-120">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a12b-121">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="4a12b-121">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="4a12b-122">Popisuje, jak vytvořit relace mezi tabulkami v <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-122">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a12b-123">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="4a12b-123">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="4a12b-124">Popisuje, jak použít relace mezi tabulkami v <xref:System.Data.DataSet> k vrácení podřízených nebo nadřazených řádků relace typu nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="4a12b-124">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="4a12b-125">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-125">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="4a12b-126">Popisuje, jak sloučit obsah jednoho <xref:System.Data.DataSet> , <xref:System.Data.DataTable> nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-126">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4a12b-127">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-127">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="4a12b-128">Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> , která může obsahovat schéma i zadaná data.</span><span class="sxs-lookup"><span data-stu-id="4a12b-128">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="4a12b-129">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-129">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="4a12b-130">Popisuje události <xref:System.Data.DataSet> a, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="4a12b-130">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="4a12b-131">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-131">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="4a12b-132">Popisuje <xref:System.Data.DataSet> , co je typu a jak ho vytvořit a použít.</span><span class="sxs-lookup"><span data-stu-id="4a12b-132">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="4a12b-133">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="4a12b-133">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="4a12b-134">Popisuje, jak vytvořit <xref:System.Data.DataTable> , definovat schéma a manipulovat s daty.</span><span class="sxs-lookup"><span data-stu-id="4a12b-134">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="4a12b-135">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="4a12b-135">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="4a12b-136">Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-136">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="4a12b-137">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4a12b-137">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="4a12b-138">Popisuje, jak vytvořit a pracovat s `DataViews` událostmi a pracovat s nimi <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="4a12b-138">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="4a12b-139">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="4a12b-139">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="4a12b-140">Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a uchování obsahu <xref:System.Data.DataSet> jako XML data.</span><span class="sxs-lookup"><span data-stu-id="4a12b-140">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="4a12b-141">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="4a12b-141">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="4a12b-142">Popisuje, jak vytvořit webovou službu XML, která používá <xref:System.Data.DataSet> k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="4a12b-142">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4a12b-143">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4a12b-143">Related Sections</span></span>  
 [<span data-ttu-id="4a12b-144">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a12b-144">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="4a12b-145">Přináší nové funkce, které jsou v ADO.NET novinkou.</span><span class="sxs-lookup"><span data-stu-id="4a12b-145">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="4a12b-146">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a12b-146">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="4a12b-147">Poskytuje Úvod k návrhu a součástem ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4a12b-147">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="4a12b-148">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="4a12b-148">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="4a12b-149">Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4a12b-149">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="4a12b-150">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="4a12b-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="4a12b-151">Popisuje, jak vyřešit změny dat v datové **sadě** zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4a12b-151">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="4a12b-152">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="4a12b-152">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="4a12b-153">Popisuje, jak naplnit **datovou sadu** pomocí informací o primárním klíči ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4a12b-153">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a12b-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a12b-154">See also</span></span>

- [<span data-ttu-id="4a12b-155">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a12b-155">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="4a12b-156">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a12b-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
