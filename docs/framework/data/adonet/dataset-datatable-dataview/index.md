---
title: Datové sady, datové tabulky a datová zobrazení
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: d712f82b0d776b671a8d8219276c32761d245047
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521280"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="68adb-102">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="68adb-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="68adb-103">ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace dat, která poskytuje relační konzistentní programovací model bez ohledu na zdroj dat obsahuje.</span><span class="sxs-lookup"><span data-stu-id="68adb-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="68adb-104">A <xref:System.Data.DataSet> představuje ucelenou sadu dat včetně tabulek, které obsahují, pořadí a omezit data, jakož i relace mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="68adb-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="68adb-105">Práce s několika způsoby <xref:System.Data.DataSet>, který je možné použít samostatně nebo v kombinaci.</span><span class="sxs-lookup"><span data-stu-id="68adb-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="68adb-106">Můžete:</span><span class="sxs-lookup"><span data-stu-id="68adb-106">You can:</span></span>  
  
-   <span data-ttu-id="68adb-107">Prostřednictvím kódu programu vytvořit <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, a <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulek daty.</span><span class="sxs-lookup"><span data-stu-id="68adb-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="68adb-108">Naplnění <xref:System.Data.DataSet> s tabulkami dat z existujícího zdroje relačních dat pomocí `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="68adb-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="68adb-109">Načtení a uložení <xref:System.Data.DataSet> obsah pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="68adb-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="68adb-110">Další informace najdete v tématu [použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="68adb-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="68adb-111">Silného typu <xref:System.Data.DataSet> může taky přenášet pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="68adb-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="68adb-112">Návrh <xref:System.Data.DataSet> je ideální pro přenos dat pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="68adb-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="68adb-113">Přehled webových služeb XML, naleznete v tématu [přehled webových služeb XML](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="68adb-113">For an overview of XML Web services, see [XML Web Services Overview](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="68adb-114">Příklad použití <xref:System.Data.DataSet> z webové služby XML, naleznete v tématu [spotřebování datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="68adb-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68adb-115">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="68adb-115">In This Section</span></span>  
 [<span data-ttu-id="68adb-116">Vytvoření datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="68adb-117">Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68adb-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68adb-118">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="68adb-119">Popisuje, jak vytvořit a přidat tabulky a sloupce, které chcete <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68adb-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68adb-120">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="68adb-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="68adb-121">Popisuje postup vytvoření vztahů mezi tabulkami <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68adb-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68adb-122">Navigace v datových relacích</span><span class="sxs-lookup"><span data-stu-id="68adb-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="68adb-123">Popisuje způsob použití vztahy mezi tabulkami <xref:System.Data.DataSet> vrátit podřízeného nebo nadřazeného řádky v relaci nadřazený podřízený.</span><span class="sxs-lookup"><span data-stu-id="68adb-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="68adb-124">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="68adb-125">Popisuje, jak sloučit obsah jednoho <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68adb-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68adb-126">Kopírování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="68adb-127">Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> , který může obsahovat schéma, jakož i zadaná data.</span><span class="sxs-lookup"><span data-stu-id="68adb-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="68adb-128">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="68adb-129">Popisuje událostí <xref:System.Data.DataSet> a způsob jejich použití.</span><span class="sxs-lookup"><span data-stu-id="68adb-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="68adb-130">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="68adb-131">Popisuje, jaké typovaného <xref:System.Data.DataSet> je a jak vytvořit a používat ho.</span><span class="sxs-lookup"><span data-stu-id="68adb-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="68adb-132">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="68adb-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="68adb-133">Popisuje, jak vytvořit <xref:System.Data.DataTable>, definovat schéma a manipulaci s daty.</span><span class="sxs-lookup"><span data-stu-id="68adb-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="68adb-134">Čtečky datových tabulek</span><span class="sxs-lookup"><span data-stu-id="68adb-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="68adb-135">Popisuje, jak vytvořit a používat <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="68adb-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="68adb-136">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="68adb-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="68adb-137">Popisuje, jak vytvořit a pracovat s `DataViews` a pracovat s <xref:System.Data.DataView> události.</span><span class="sxs-lookup"><span data-stu-id="68adb-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="68adb-138">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="68adb-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="68adb-139">Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a při zachování obsahu <xref:System.Data.DataSet> jako XML data.</span><span class="sxs-lookup"><span data-stu-id="68adb-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="68adb-140">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="68adb-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="68adb-141">Popisuje, jak vytvořit webové služby XML, který používá <xref:System.Data.DataSet> k přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="68adb-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="68adb-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="68adb-142">Related Sections</span></span>  
 [<span data-ttu-id="68adb-143">Novinky v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68adb-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="68adb-144">Představuje funkce, které jsou nové v rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="68adb-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="68adb-145">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68adb-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="68adb-146">Poskytuje úvod do navrhování a komponenty rozhraní ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="68adb-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="68adb-147">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="68adb-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="68adb-148">Popisuje, jak načíst **datovou sadu** s daty z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="68adb-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="68adb-149">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="68adb-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="68adb-150">Popisuje, jak vyřešit změny dat v **datovou sadu** zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="68adb-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="68adb-151">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="68adb-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="68adb-152">Popisuje, jak naplnit **datovou sadu** s informacemi o primárním klíči ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="68adb-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68adb-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68adb-153">See also</span></span>
- [<span data-ttu-id="68adb-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68adb-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="68adb-155">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="68adb-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
