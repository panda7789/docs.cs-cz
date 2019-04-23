---
title: DataGridView – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
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
ms.openlocfilehash: 095c89fd305b1eeb73e2919760abe48e848c6aa0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112876"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="7dd6f-102">DataGridView – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7dd6f-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="7dd6f-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7dd6f-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7dd6f-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="7dd6f-105">S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="7dd6f-106">Vazba dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku je jednoduchý a intuitivní a v mnoha případech je stejně jednoduché jako nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="7dd6f-107">Když se navážete na zdroj dat, který obsahuje více seznamů a tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> nastavte na řetězec, který určuje seznam nebo tabulku k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="7dd6f-108"><xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje standardní Windows Forms datový model vazby, proto vytvoří vazbu instance tříd, které je popsáno v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="7dd6f-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="7dd6f-109">Všechny třídy, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="7dd6f-110">Všechny třídy, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, jako <xref:System.Data.DataTable> a <xref:System.Data.DataSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="7dd6f-111">Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, jako <xref:System.ComponentModel.BindingList%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="7dd6f-112">Všechny třídy, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, jako <xref:System.Windows.Forms.BindingSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="7dd6f-113"><xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje datové vazby k veřejné vlastnosti objektů vrácených podle těchto rozhraní a vlastnosti kolekci vrácené poskytovatelem <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, je-li implementovat na vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="7dd6f-114">Obvykle vytvoří vazbu k <xref:System.Windows.Forms.BindingSource> komponenty a vazby <xref:System.Windows.Forms.BindingSource> komponentu do jiného zdroje dat, nebo přidejte do ní pro obchodní objekty.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="7dd6f-115"><xref:System.Windows.Forms.BindingSource> Komponenta je upřednostňovaný zdroj, protože můžete vázat na širokou škálu zdrojů dat a můžete vyřešit řadu problémů vazby dat automaticky.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="7dd6f-116">Další informace najdete v tématu [komponenty BindingSource](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="7dd6f-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="7dd6f-117"><xref:System.Windows.Forms.DataGridView> Ovládací prvek lze také v *nevázaného* režimu s žádná základní data store.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="7dd6f-118">Příklad kódu, který používá nevázaný <xref:System.Windows.Forms.DataGridView> řídí, najdete v článku [názorný postup: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7dd6f-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="7dd6f-119"><xref:System.Windows.Forms.DataGridView> Ovládací prvek je vysoce konfigurovatelné a rozšiřitelné, a poskytuje mnoho vlastnosti, metody a události přizpůsobit její vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="7dd6f-120">Pokud chcete aplikaci Windows Forms k zobrazení tabulky dat, zvažte použití <xref:System.Windows.Forms.DataGridView> ovládací prvek před ostatními (například <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="7dd6f-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="7dd6f-121">Pokud zobrazujete Jemná mřížka jen pro čtení hodnot, nebo pokud chcete povolit uživatelům upravit tabulku s milióny záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne řešení snadno programovatelná, efektivně využívajícího paměť.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7dd6f-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7dd6f-122">In This Section</span></span>  
 [<span data-ttu-id="7dd6f-123">Souhrn technologie ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="7dd6f-124">Shrnuje <xref:System.Windows.Forms.DataGridView> řídit koncepty a používání související třídy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="7dd6f-125">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="7dd6f-126">Popisuje architekturu <xref:System.Windows.Forms.DataGridView> ovládacího prvku, s vysvětlením, její typ struktura hierarchie a dědičnost.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="7dd6f-127">Scénáře ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="7dd6f-128">Popisuje nejběžnější scénáře, ve kterém <xref:System.Windows.Forms.DataGridView> ovládací prvky se používají.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="7dd6f-129">Adresář kódu ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="7dd6f-130">Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="7dd6f-131">Tyto příklady jsou rozděleny podle typu úlohy.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7dd6f-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7dd6f-132">Related Sections</span></span>  
 [<span data-ttu-id="7dd6f-133">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dd6f-134">Tento článek popisuje typy sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek použitý k zobrazení informací a umožní uživatelům změnit nebo přidat informace.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="7dd6f-135">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dd6f-136">Obsahuje témata, které popisují, jak ručně, nebo z externího zdroje dat naplnění ovládacího prvku s daty.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="7dd6f-137">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dd6f-138">Obsahuje témata, které popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozené buňky, sloupce a typy řádků.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="7dd6f-139">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dd6f-140">Obsahuje témata, které popisují, jak pomocí efektivně se vyhnout problémům s výkonem při práci s velkými objemy dat ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7dd6f-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd6f-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dd6f-141">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7dd6f-142">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="7dd6f-143">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7dd6f-144">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7dd6f-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
