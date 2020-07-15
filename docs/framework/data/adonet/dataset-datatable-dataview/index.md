---
title: Datové sady, datové tabulky a datová zobrazení
description: Seznamte se s různými způsoby, jak pracovat s datovou sadou ADO.NET, což je reprezentace dat rezidentních v paměti, která poskytuje konzistentní relační programovací model.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 53e12f701b9be1938d62f46bbeb6e63d95c03386
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374504"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="17490-103">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="17490-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="17490-104">ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="17490-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="17490-105"><xref:System.Data.DataSet>Představuje kompletní sadu dat, včetně tabulek, které obsahují, vyřazení a omezení dat a také vztahů mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="17490-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="17490-106">Existuje několik způsobů práce s a <xref:System.Data.DataSet> , které lze použít nezávisle nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="17490-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="17490-107">Můžete:</span><span class="sxs-lookup"><span data-stu-id="17490-107">You can:</span></span>  
  
- <span data-ttu-id="17490-108">Programové vytvoření <xref:System.Data.DataTable> , a <xref:System.Data.DataRelation> <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulek daty.</span><span class="sxs-lookup"><span data-stu-id="17490-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="17490-109">Naplňte <xref:System.Data.DataSet> tabulky daty z existujícího relačního zdroje dat pomocí `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="17490-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="17490-110">Načtěte a zachovejte <xref:System.Data.DataSet> obsah pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="17490-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="17490-111">Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="17490-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="17490-112">Silné typy <xref:System.Data.DataSet> lze také přenést pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="17490-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="17490-113">Návrh je <xref:System.Data.DataSet> ideální pro přenos dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="17490-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="17490-114">Přehled webových služeb XML najdete v tématu [Přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="17490-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="17490-115">Příklad použití <xref:System.Data.DataSet> webové služby XML naleznete v tématu [spotřebovávání datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="17490-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17490-116">V této části</span><span class="sxs-lookup"><span data-stu-id="17490-116">In this section</span></span>

 [<span data-ttu-id="17490-117">Doprovodné materiály k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="17490-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="17490-118">Poskytuje bezpečnostní pokyny pro <xref:System.Data.DataSet> a <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="17490-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="17490-119">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="17490-120">Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="17490-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="17490-121">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="17490-122">Popisuje, jak vytvořit a přidat tabulky a sloupce do <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="17490-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="17490-123">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="17490-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="17490-124">Popisuje, jak vytvořit relace mezi tabulkami v <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="17490-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="17490-125">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="17490-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="17490-126">Popisuje, jak použít relace mezi tabulkami v <xref:System.Data.DataSet> k vrácení podřízených nebo nadřazených řádků relace typu nadřazený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="17490-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="17490-127">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="17490-128">Popisuje, jak sloučit obsah jednoho <xref:System.Data.DataSet> , <xref:System.Data.DataTable> nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="17490-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="17490-129">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="17490-130">Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> , která může obsahovat schéma i zadaná data.</span><span class="sxs-lookup"><span data-stu-id="17490-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="17490-131">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="17490-132">Popisuje události <xref:System.Data.DataSet> a, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="17490-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="17490-133">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="17490-134">Popisuje <xref:System.Data.DataSet> , co je typu a jak ho vytvořit a použít.</span><span class="sxs-lookup"><span data-stu-id="17490-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="17490-135">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="17490-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="17490-136">Popisuje, jak vytvořit <xref:System.Data.DataTable> , definovat schéma a manipulovat s daty.</span><span class="sxs-lookup"><span data-stu-id="17490-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="17490-137">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="17490-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="17490-138">Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="17490-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="17490-139">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="17490-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="17490-140">Popisuje, jak vytvořit a pracovat s `DataViews` událostmi a pracovat s nimi <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="17490-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="17490-141">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="17490-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="17490-142">Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a uchování obsahu <xref:System.Data.DataSet> jako XML data.</span><span class="sxs-lookup"><span data-stu-id="17490-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="17490-143">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="17490-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="17490-144">Popisuje, jak vytvořit webovou službu XML, která používá <xref:System.Data.DataSet> k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="17490-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17490-145">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="17490-145">Related sections</span></span>

 [<span data-ttu-id="17490-146">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17490-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="17490-147">Přináší nové funkce, které jsou v ADO.NET novinkou.</span><span class="sxs-lookup"><span data-stu-id="17490-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="17490-148">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17490-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="17490-149">Poskytuje Úvod k návrhu a součástem ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="17490-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="17490-150">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="17490-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="17490-151">Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="17490-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="17490-152">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="17490-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="17490-153">Popisuje, jak vyřešit změny dat v datové **sadě** zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="17490-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="17490-154">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="17490-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="17490-155">Popisuje, jak naplnit **datovou sadu** pomocí informací o primárním klíči ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="17490-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17490-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="17490-156">See also</span></span>

- [<span data-ttu-id="17490-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17490-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="17490-158">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17490-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
