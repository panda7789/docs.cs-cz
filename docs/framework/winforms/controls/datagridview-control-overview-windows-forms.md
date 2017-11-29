---
title: "DataGridView – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4209866f63931fb3d80f35e211bd5f9b35ed48bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="f2689-102">DataGridView – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f2689-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="f2689-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="f2689-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f2689-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f2689-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f2689-105">Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zobrazit a upravit tabulková data z mnoha různých datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="f2689-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="f2689-106">Vazba dat k <xref:System.Windows.Forms.DataGridView> ovládací prvek je jednoduché a intuitivní a v mnoha případech je jednoduché, nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f2689-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="f2689-107">Při vytvoření vazby ke zdroji dat, která obsahuje více seznamů nebo tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> vlastnost na řetězec, který určuje seznamu nebo tabulky pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f2689-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="f2689-108"><xref:System.Windows.Forms.DataGridView> Řízení podporuje standardní Windows Forms datový model vazby, tak ho vytvoří vazbu k instance tříd, které jsou popsané v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="f2689-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="f2689-109">Všechny třídy, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="f2689-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="f2689-110">Všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, jako <xref:System.Data.DataTable> a <xref:System.Data.DataSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="f2689-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="f2689-111">Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, například <xref:System.ComponentModel.BindingList%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="f2689-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="f2689-112">Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, například <xref:System.Windows.Forms.BindingSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="f2689-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="f2689-113"><xref:System.Windows.Forms.DataGridView> Řízení podporuje datovou vazbu veřejné vlastnosti objektů vrácených z těchto rozhraní a vlastnosti kolekce vrácené <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, pokud se implementuje na vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="f2689-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="f2689-114">Obvykle vytvoří vazbu k <xref:System.Windows.Forms.BindingSource> součásti a vazby <xref:System.Windows.Forms.BindingSource> součásti do jiného zdroje dat, nebo jeho naplnění objekty firmy.</span><span class="sxs-lookup"><span data-stu-id="f2689-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="f2689-115"><xref:System.Windows.Forms.BindingSource> Součást je zdroj dat upřednostňované, protože lze vázat k široké škále zdrojů dat a může vyřešit řadu problémů vazby dat automaticky.</span><span class="sxs-lookup"><span data-stu-id="f2689-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="f2689-116">Další informace najdete v tématu [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="f2689-116">For more information, see [BindingSource Component](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="f2689-117"><xref:System.Windows.Forms.DataGridView> Řízení lze také v *nevázaný* režimu s žádné příslušné datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="f2689-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="f2689-118">Pro příklad kódu, který se používá nevázaný <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [návod: vytváření nevázaný ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f2689-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f2689-119"><xref:System.Windows.Forms.DataGridView> Řízení je vysoce Konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí přizpůsobit její vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="f2689-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="f2689-120">Když chcete aplikaci Windows Forms k zobrazení tabulková data, zvažte použití <xref:System.Windows.Forms.DataGridView> řízení před jiné (například <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="f2689-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="f2689-121">Pokud jsou zobrazení malé mřížky hodnot jen pro čtení, nebo pokud chcete povolit uživatelům upravit tabulku s miliony záznamů, <xref:System.Windows.Forms.DataGridView> řízení vám poskytne snadno programovatelná a paměti efektivní řešení.</span><span class="sxs-lookup"><span data-stu-id="f2689-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2689-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f2689-122">In This Section</span></span>  
 [<span data-ttu-id="f2689-123">Souhrn technologie ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-123">DataGridView Control Technology Summary</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="f2689-124">Shrnuje <xref:System.Windows.Forms.DataGridView> řízení konceptech a použití související třídy.</span><span class="sxs-lookup"><span data-stu-id="f2689-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="f2689-125">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-125">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="f2689-126">Popisuje architekturu <xref:System.Windows.Forms.DataGridView> řízení, vysvětlením struktura hierarchie a dědičnost jeho typu.</span><span class="sxs-lookup"><span data-stu-id="f2689-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="f2689-127">Scénáře ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-127">DataGridView Control Scenarios</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="f2689-128">Popisuje nejběžnější scénáře, ve kterém <xref:System.Windows.Forms.DataGridView> ovládací prvky jsou používány.</span><span class="sxs-lookup"><span data-stu-id="f2689-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="f2689-129">Adresář kódu ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-129">DataGridView Control Code Directory</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="f2689-130">Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy.</span><span class="sxs-lookup"><span data-stu-id="f2689-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="f2689-131">Tyto příklady jsou klasifikovány podle typu úlohy.</span><span class="sxs-lookup"><span data-stu-id="f2689-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f2689-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f2689-132">Related Sections</span></span>  
 [<span data-ttu-id="f2689-133">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-133">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f2689-134">Popisuje typy sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek použitý k zobrazení informací a povolit uživatelům změnit nebo přidat informace.</span><span class="sxs-lookup"><span data-stu-id="f2689-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="f2689-135">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f2689-136">Obsahuje témata, která popisují, jak buď ručně, nebo z externího zdroje dat naplnit ovládací prvek s daty.</span><span class="sxs-lookup"><span data-stu-id="f2689-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="f2689-137">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f2689-137">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f2689-138">Obsahuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.</span><span class="sxs-lookup"><span data-stu-id="f2689-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="f2689-139">Ladění výkonu v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f2689-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f2689-140">Obsahuje témata, která popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkými objemy dat.</span><span class="sxs-lookup"><span data-stu-id="f2689-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2689-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2689-141">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="f2689-142">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f2689-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="f2689-143">Výchozí funkce v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f2689-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f2689-144">Výchozí zpracování v ovládacím prvku Windows Forms DataGridView klávesnice a myši</span><span class="sxs-lookup"><span data-stu-id="f2689-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
