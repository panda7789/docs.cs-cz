---
title: DataView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5b79461a6fc3314ca4178e0f9b1cff1c468cc3e6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="dataviews"></a><span data-ttu-id="4e1e5-102">DataView</span><span class="sxs-lookup"><span data-stu-id="4e1e5-102">DataViews</span></span>
<span data-ttu-id="4e1e5-103">A <xref:System.Data.DataView> umožňuje vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, funkci, která se často používá v aplikacích datové vazby.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="4e1e5-104">Použití **DataView**, můžou zpřístupnit data v tabulce s různým řazením a data lze filtrovat podle řádku stavu nebo podle výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="4e1e5-105">A **DataView** poskytuje dynamické zobrazení dat v základní **DataTable**: obsah, řazení a členství projevily změny, kdy k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="4e1e5-106">Toto chování se liší od **vyberte** metodu **DataTable**, která vrátí <xref:System.Data.DataRow> pole z tabulky podle konkrétní pořadí filtrů a řazení: thiscontent odráží změny základní tabulku, ale jeho členství a řazení zůstat statický.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="4e1e5-107">Dynamické schopnosti **DataView** zkontrolujte ideální pro vazby dat aplikací.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="4e1e5-108">A **DataView** poskytuje dynamické zobrazení jednu sadu dat, podobně jako zobrazení databáze, do které můžete použít jiné řazení a filtrování kritéria.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="4e1e5-109">Na rozdíl od zobrazení databáze, ale **DataView** nemůže být považované za tabulky a zobrazení spojené tabulky nelze zadat.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="4e1e5-110">Také nelze vyloučit sloupce, které existují ve zdrojové tabulce, ani připojit sloupce, např. výpočetní sloupců, které nejsou k dispozici ve zdrojové tabulce.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="4e1e5-111">Můžete použít <xref:System.Data.DataView.DataViewManager%2A> ke správě nastavení zobrazení pro všechny tabulky v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="4e1e5-112">**DataViewManager** vám poskytne pohodlný způsob, jak spravovat výchozí nastavení zobrazení pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="4e1e5-113">Při vytváření vazby ovládacího prvku k více než jednu tabulku **datovou sadu**, závazný k **DataViewManager** je ideální volbou.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e1e5-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4e1e5-114">In This Section</span></span>  
 [<span data-ttu-id="4e1e5-115">Vytvoření zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4e1e5-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="4e1e5-116">Popisuje postup vytvoření **DataView** pro **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="4e1e5-117">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="4e1e5-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="4e1e5-118">Popisuje, jak nastavit vlastnosti **DataView** vrátit podmnožiny dat řádků kritéria filtru konkrétní schůzky, nebo vrátit data v konkrétní řazení.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="4e1e5-119">DataRows a DataRowViews</span><span class="sxs-lookup"><span data-stu-id="4e1e5-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="4e1e5-120">Popisuje, jak získat přístup k datům vystavené **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="4e1e5-121">Hledání řádků</span><span class="sxs-lookup"><span data-stu-id="4e1e5-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="4e1e5-122">Popisuje, jak k vyhledání konkrétního řádku **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="4e1e5-123">ChildViews a relace</span><span class="sxs-lookup"><span data-stu-id="4e1e5-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="4e1e5-124">Popisuje postup vytvoření zobrazení dat pomocí relaci nadřazený podřízený **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="4e1e5-125">Úpravy zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4e1e5-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="4e1e5-126">Popisuje, jak upravit data v podkladové **DataTable** prostřednictvím **DataView**, včetně povolení nebo zakázání aktualizací.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="4e1e5-127">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4e1e5-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="4e1e5-128">Popisuje způsob použití **ListChanged** událostí pro příjem oznámení při obsah nebo pořadí **DataView** se právě aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="4e1e5-129">Správa zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4e1e5-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="4e1e5-130">Popisuje způsob použití **DataViewManager** ke správě **DataView** nastavení pro každou tabulku v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e1e5-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4e1e5-131">Related Sections</span></span>  
 [<span data-ttu-id="4e1e5-132">Webových aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4e1e5-132">ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="4e1e5-133">Poskytuje přehled a podrobné postupy pro vytváření aplikací ASP.NET, webových formulářů a webových služeb.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="4e1e5-134">Aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="4e1e5-134">Windows Applications</span></span>](http://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="4e1e5-135">Poskytuje podrobné informace o práci s Windows Forms a konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="4e1e5-136">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="4e1e5-136">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="4e1e5-137">Popisuje **datovou sadu** objekt a jak můžete použít ke správě dat aplikací.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="4e1e5-138">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="4e1e5-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="4e1e5-139">Popisuje **DataTable** objekt a jak můžete použít ke správě dat aplikace, samostatně nebo jako součást **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="4e1e5-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e1e5-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="4e1e5-141">Popisuje technologie ADO.NET architektura a komponenty a jak používat technologie ADO.NET pro přístup k existující zdroje dat a spravovat data aplikací.</span><span class="sxs-lookup"><span data-stu-id="4e1e5-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1e5-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e1e5-142">See Also</span></span>  
 [<span data-ttu-id="4e1e5-143">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4e1e5-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
