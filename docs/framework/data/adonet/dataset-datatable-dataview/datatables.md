---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d1222d3df30bf2b3de1761b8fa5c702dc687d0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="datatables"></a><span data-ttu-id="cacad-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="cacad-102">DataTables</span></span>
<span data-ttu-id="cacad-103">A <xref:System.Data.DataSet> se skládá z kolekce tabulek, vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="cacad-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="cacad-104">V technologii ADO.NET <xref:System.Data.DataTable> objekty se používají k vyjádření tabulky v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="cacad-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="cacad-105">A **DataTable** představuje jednu tabulku v paměti relačních dat; je místní pro data. Aplikace založené na NET, ve kterém se nachází, ale je možné importovat ze zdroje dat, například pomocí systému Microsoft SQL Server **DataAdapter** Další informace najdete v tématu [naplňování datové sady z modul DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .</span><span class="sxs-lookup"><span data-stu-id="cacad-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="cacad-106">**DataTable** třída je členem skupiny **System.Data** oboru názvů v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cacad-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="cacad-107">Můžete vytvořit a použít **DataTable** samostatně nebo jako člen skupiny **datovou sadu**, a **DataTable** objekty lze také použít ve spojení s jinými objekty rozhraní .NET Framework včetně <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="cacad-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="cacad-108">Přístup kolekce tabulek v **datovou sadu** prostřednictvím **tabulky** vlastnost **datovou sadu** objektu.</span><span class="sxs-lookup"><span data-stu-id="cacad-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="cacad-109">Schéma a struktura tabulky je reprezentována sloupce a omezení.</span><span class="sxs-lookup"><span data-stu-id="cacad-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="cacad-110">Můžete definovat schéma **DataTable** pomocí <xref:System.Data.DataColumn> objekty a také <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty.</span><span class="sxs-lookup"><span data-stu-id="cacad-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="cacad-111">Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují počítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnot primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="cacad-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="cacad-112">Kromě schématu **DataTable** musí mít také řádky, které obsahují a pořadí data.</span><span class="sxs-lookup"><span data-stu-id="cacad-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="cacad-113"><xref:System.Data.DataRow> Třída reprezentuje skutečný data obsažená v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cacad-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="cacad-114">Můžete použít **DataRow** a jeho vlastnosti a metody k načtení, hodnocení a pracovat s daty v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cacad-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="cacad-115">Při přístupu a při změně data v řádku, **DataRow** objekt udržovat její aktuální a původní stav.</span><span class="sxs-lookup"><span data-stu-id="cacad-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="cacad-116">Můžete vytvořit nadřazený podřízený relace mezi tabulkami pomocí jednoho nebo více souvisejících sloupců v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="cacad-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="cacad-117">Vytvoření vztahu mezi **DataTable** objekty pomocí <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="cacad-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="cacad-118">**DataRelation** objekty pak lze vrátit řádky v relaci nadřazená nebo podřízená konkrétního řádku.</span><span class="sxs-lookup"><span data-stu-id="cacad-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="cacad-119">Další informace najdete v tématu [přidání DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="cacad-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cacad-120">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cacad-120">In This Section</span></span>  
 [<span data-ttu-id="cacad-121">Vytváření DataTable</span><span class="sxs-lookup"><span data-stu-id="cacad-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="cacad-122">Vysvětluje, jak vytvořit **DataTable** a přidejte ho do **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="cacad-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="cacad-123">Definice schématu DataTable</span><span class="sxs-lookup"><span data-stu-id="cacad-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="cacad-124">Poskytuje informace o vytváření a používání **DataColumn** objekty a omezení.</span><span class="sxs-lookup"><span data-stu-id="cacad-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="cacad-125">Manipulace s daty v DataTable</span><span class="sxs-lookup"><span data-stu-id="cacad-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="cacad-126">Vysvětluje, jak přidat, upravit a odstranit data v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cacad-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="cacad-127">Vysvětluje, jak používat **DataTable** událostí k prozkoumání změny dat v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cacad-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="cacad-128">Zpracování událostí DataTable</span><span class="sxs-lookup"><span data-stu-id="cacad-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="cacad-129">Poskytuje informace o událostech, které jsou k dispozici pro použití s **DataTable**, včetně událostí při změně hodnoty sloupců a řádků se přidají nebo odstranit.</span><span class="sxs-lookup"><span data-stu-id="cacad-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cacad-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cacad-130">Related Sections</span></span>  
 [<span data-ttu-id="cacad-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cacad-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="cacad-132">Popisuje technologie ADO.NET architektura a komponenty a jak je používat pro přístup k existující zdroje dat a spravovat data aplikací.</span><span class="sxs-lookup"><span data-stu-id="cacad-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="cacad-133">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="cacad-133">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="cacad-134">Poskytuje informace o technologie ADO.NET **datovou sadu** včetně toho, jak vytvořit relace mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="cacad-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="cacad-135">Poskytuje referenční informace o **omezení** objektu.</span><span class="sxs-lookup"><span data-stu-id="cacad-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="cacad-136">Poskytuje referenční informace o **DataColumn** objektu.</span><span class="sxs-lookup"><span data-stu-id="cacad-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="cacad-137">Poskytuje referenční informace o **datovou sadu** objektu.</span><span class="sxs-lookup"><span data-stu-id="cacad-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="cacad-138">Poskytuje referenční informace o **DataTable** objektu.</span><span class="sxs-lookup"><span data-stu-id="cacad-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="cacad-139">Přehled knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="cacad-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="cacad-140">Najdete zde přehled knihovny tříd rozhraní .NET Framework, včetně **systému** obor názvů a také její obor názvů druhé úrovně **System.Data**.</span><span class="sxs-lookup"><span data-stu-id="cacad-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacad-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="cacad-141">See Also</span></span>  
 [<span data-ttu-id="cacad-142">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="cacad-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
