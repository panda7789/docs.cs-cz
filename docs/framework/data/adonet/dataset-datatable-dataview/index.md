---
title: Datové sady, datové tabulky a datová zobrazení
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 2303b0ce9bc8b389a3a7af9e8fcfbcb13d0007ae
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759485"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="aa318-102">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="aa318-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="aa318-103">Technologie ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace data, která zajišťuje konzistentní relační programovací model bez ohledu na zdroj dat obsahuje.</span><span class="sxs-lookup"><span data-stu-id="aa318-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="aa318-104">A <xref:System.Data.DataSet> představuje kompletní sadu dat včetně tabulek, které obsahují, řazení a omezit data, jakož i relace mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="aa318-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="aa318-105">Práce s několika způsoby <xref:System.Data.DataSet>, který je možné použít samostatně nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="aa318-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="aa318-106">Můžeš:</span><span class="sxs-lookup"><span data-stu-id="aa318-106">You can:</span></span>  
  
-   <span data-ttu-id="aa318-107">Vytváření prostřednictvím kódu programu <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, a <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulky s daty.</span><span class="sxs-lookup"><span data-stu-id="aa318-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="aa318-108">Naplnění <xref:System.Data.DataSet> s tabulkami dat z existujícího zdroje relačních dat systémem `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="aa318-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="aa318-109">Načtení a zachovat <xref:System.Data.DataSet> obsah pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="aa318-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="aa318-110">Další informace najdete v tématu [pomocí XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="aa318-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="aa318-111">Silného typu <xref:System.Data.DataSet> můžete také přenosu pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="aa318-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="aa318-112">Návrh <xref:System.Data.DataSet> je ideální pro přenos dat pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="aa318-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="aa318-113">Přehled webové služby XML, najdete v části [Přehled webové služby XML](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="aa318-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="aa318-114">Příklad použití <xref:System.Data.DataSet> z webové služby XML, najdete na stránce [využívání datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="aa318-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa318-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa318-115">In This Section</span></span>  
 [<span data-ttu-id="aa318-116">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="aa318-117">Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="aa318-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="aa318-118">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="aa318-119">Popisuje postup vytvoření a přidání tabulek a sloupců <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="aa318-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="aa318-120">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="aa318-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="aa318-121">Popisuje postup vytvoření relace mezi tabulkami <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="aa318-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="aa318-122">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="aa318-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="aa318-123">Popisuje, jak použít vztahy mezi tabulkami <xref:System.Data.DataSet> vrátit nadřazená nebo podřízená řádky relaci nadřazený podřízený.</span><span class="sxs-lookup"><span data-stu-id="aa318-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="aa318-124">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="aa318-125">Popisuje, jak sloučit obsah jedné <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do jiné <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="aa318-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="aa318-126">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="aa318-127">Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> obsahující schématu, jakož i zadaná data.</span><span class="sxs-lookup"><span data-stu-id="aa318-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="aa318-128">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="aa318-129">Popisuje události z <xref:System.Data.DataSet> a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="aa318-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="aa318-130">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="aa318-131">Popisuje, co představuje zadaný <xref:System.Data.DataSet> je a o tom, jak vytvořit a používat ho.</span><span class="sxs-lookup"><span data-stu-id="aa318-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="aa318-132">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="aa318-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="aa318-133">Popisuje postup vytvoření <xref:System.Data.DataTable>, definovat schéma a pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="aa318-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="aa318-134">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="aa318-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="aa318-135">Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="aa318-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="aa318-136">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="aa318-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="aa318-137">Popisuje postup vytváření a práci s `DataViews` a pracovat s <xref:System.Data.DataView> události.</span><span class="sxs-lookup"><span data-stu-id="aa318-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="aa318-138">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="aa318-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="aa318-139">Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a zachování obsahu <xref:System.Data.DataSet> jako XML data.</span><span class="sxs-lookup"><span data-stu-id="aa318-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="aa318-140">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="aa318-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="aa318-141">Popisuje postup vytvoření XML webové služby, který používá <xref:System.Data.DataSet> k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="aa318-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa318-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa318-142">Related Sections</span></span>  
 [<span data-ttu-id="aa318-143">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa318-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="aa318-144">Nabízí funkce, které nově jsou v technologii ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="aa318-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="aa318-145">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa318-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="aa318-146">Poskytuje úvod do návrhu a součástí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="aa318-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="aa318-147">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="aa318-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="aa318-148">Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="aa318-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="aa318-149">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="aa318-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="aa318-150">Popisuje, jak vyřešit změny k datům ve **datovou sadu** zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="aa318-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="aa318-151">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="aa318-152">Popisuje, jak k naplnění **datovou sadu** s primární klíče informace ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="aa318-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa318-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa318-153">See Also</span></span>  
 [<span data-ttu-id="aa318-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa318-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="aa318-155">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="aa318-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
