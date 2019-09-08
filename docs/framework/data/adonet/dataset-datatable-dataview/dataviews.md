---
title: Zobrazení dat
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786342"
---
# <a name="dataviews"></a><span data-ttu-id="c991f-102">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c991f-102">DataViews</span></span>
<span data-ttu-id="c991f-103">Umožňuje vytvářet různá zobrazení dat uložených <xref:System.Data.DataTable>v nástroji, což je funkce, která se často používá v aplikacích s datovou vazbou. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="c991f-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="c991f-104">Pomocí objektu **DataView**můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru.</span><span class="sxs-lookup"><span data-stu-id="c991f-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="c991f-105">Zobrazení **DataView** poskytuje dynamický pohled na data v podkladovém **objektu DataTable**: obsah, řazení a členství odrážejí změny při jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="c991f-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="c991f-106">Toto chování se liší od metody **Select** **objektu DataTable**, <xref:System.Data.DataRow> která vrací pole z tabulky založené na konkrétním filtru nebo pořadí řazení: Tento obsah odráží změny v podkladové tabulce, ale její členství a řazení zůstane statické.</span><span class="sxs-lookup"><span data-stu-id="c991f-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="c991f-107">Dynamické možnosti zobrazení dat usnadňují použití datových **vazeb v aplikacích** .</span><span class="sxs-lookup"><span data-stu-id="c991f-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="c991f-108">Zobrazení **DataView** poskytuje dynamické zobrazení jedné sady dat, podobně jako zobrazení databáze, na které můžete použít různá kritéria řazení a filtrování.</span><span class="sxs-lookup"><span data-stu-id="c991f-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="c991f-109">Na rozdíl od zobrazení databáze však nelze **objekt DataView** zpracovat jako tabulku a nemůže poskytnout zobrazení spojených tabulek.</span><span class="sxs-lookup"><span data-stu-id="c991f-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="c991f-110">Nemůžete také vyloučit sloupce, které existují ve zdrojové tabulce, ani přidat sloupce, například výpočetní sloupce, které neexistují ve zdrojové tabulce.</span><span class="sxs-lookup"><span data-stu-id="c991f-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="c991f-111">Můžete použít <xref:System.Data.DataView.DataViewManager%2A> ke správě nastavení zobrazení pro všechny tabulky v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="c991f-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="c991f-112">Objekt **DataViewManager** poskytuje pohodlný způsob, jak spravovat výchozí nastavení zobrazení pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="c991f-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="c991f-113">Při vázání ovládacího prvku na více než jednu tabulku **datové sady**je ideální volbou vazba na objekt **DataViewManager** .</span><span class="sxs-lookup"><span data-stu-id="c991f-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c991f-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c991f-114">In This Section</span></span>  
 [<span data-ttu-id="c991f-115">Vytvoření zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c991f-115">Creating a DataView</span></span>](creating-a-dataview.md)  
 <span data-ttu-id="c991f-116">Popisuje, jak vytvořit **DataView** pro **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c991f-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="c991f-117">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="c991f-117">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)  
 <span data-ttu-id="c991f-118">Popisuje, jak nastavit vlastnosti objektu **DataView** tak, aby vracely podmnožiny datových řádků splňujících konkrétní kritéria filtru, nebo aby vracela data v konkrétním pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="c991f-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="c991f-119">DataRows a DataRowViews</span><span class="sxs-lookup"><span data-stu-id="c991f-119">DataRows and DataRowViews</span></span>](datarows-and-datarowviews.md)  
 <span data-ttu-id="c991f-120">Popisuje, jak získat přístup k datům vystaveným **objektem DataView**.</span><span class="sxs-lookup"><span data-stu-id="c991f-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="c991f-121">Hledání řádků</span><span class="sxs-lookup"><span data-stu-id="c991f-121">Finding Rows</span></span>](finding-rows.md)  
 <span data-ttu-id="c991f-122">Popisuje, jak najít konkrétní řádek v zobrazení **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c991f-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="c991f-123">ChildViews a relace</span><span class="sxs-lookup"><span data-stu-id="c991f-123">ChildViews and Relations</span></span>](childviews-and-relations.md)  
 <span data-ttu-id="c991f-124">Popisuje, jak vytvořit zobrazení dat z vztahu nadřazená-podřízená pomocí objektu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c991f-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="c991f-125">Úpravy zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c991f-125">Modifying DataViews</span></span>](modifying-dataviews.md)  
 <span data-ttu-id="c991f-126">Popisuje, jak upravit data v podkladovém **objektu DataTable** prostřednictvím objektu **DataView**, včetně povolení nebo zakázání aktualizací.</span><span class="sxs-lookup"><span data-stu-id="c991f-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="c991f-127">Zpracování událostí zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c991f-127">Handling DataView Events</span></span>](handling-dataview-events.md)  
 <span data-ttu-id="c991f-128">Popisuje, jak používat událost **ListChanged** k získání oznámení při aktualizaci obsahu nebo objednávky zobrazení **dat** .</span><span class="sxs-lookup"><span data-stu-id="c991f-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="c991f-129">Správa zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c991f-129">Managing DataViews</span></span>](managing-dataviews.md)  
 <span data-ttu-id="c991f-130">Popisuje, jak používat objekt **DataViewManager** **ke správě nastavení** zobrazení pro každou tabulku v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="c991f-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c991f-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c991f-131">Related Sections</span></span>  
 <span data-ttu-id="c991f-132">[ASP.NET – webové aplikace](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c991f-132">[ASP.NET Web Applications](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span></span>  
 <span data-ttu-id="c991f-133">Poskytuje přehledy a podrobné postupy pro vytváření aplikací ASP.NET, webových formulářů a webových služeb.</span><span class="sxs-lookup"><span data-stu-id="c991f-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 <span data-ttu-id="c991f-134">[Aplikace systému Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c991f-134">[Windows Applications](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span></span>  
 <span data-ttu-id="c991f-135">Poskytuje podrobné informace o práci s aplikacemi model Windows Forms a konzolových aplikací.</span><span class="sxs-lookup"><span data-stu-id="c991f-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="c991f-136">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="c991f-136">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="c991f-137">Popisuje objekt **DataSet** a způsob, jak jej můžete použít ke správě aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="c991f-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="c991f-138">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="c991f-138">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="c991f-139">Popisuje objekt **DataTable** a způsob, jak jej můžete použít ke správě dat aplikace samostatně nebo jako součást **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="c991f-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="c991f-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c991f-140">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="c991f-141">Popisuje architekturu a komponenty ADO.NET a způsob použití ADO.NET pro přístup k existujícím zdrojům dat a správě dat aplikací.</span><span class="sxs-lookup"><span data-stu-id="c991f-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c991f-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c991f-142">See also</span></span>

- [<span data-ttu-id="c991f-143">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c991f-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
