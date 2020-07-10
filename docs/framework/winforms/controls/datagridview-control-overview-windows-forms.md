---
title: DataGridView – přehled ovládacího prvku
description: Naučte se používat ovládací prvek DataGridView model Windows Forms k zobrazení a úpravám tabulkových dat z mnoha různých druhů zdrojů dat.
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
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174611"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="a0cd5-103">DataGridView – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0cd5-103">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="a0cd5-104"><xref:System.Windows.Forms.DataGridView>Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. <xref:System.Windows.Forms.DataGrid> ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-104">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a0cd5-105">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0cd5-105">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="a0cd5-106">Pomocí <xref:System.Windows.Forms.DataGridView> ovládacího prvku můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-106">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="a0cd5-107">Vázání dat na <xref:System.Windows.Forms.DataGridView> ovládací prvek je jednoduché a intuitivní a v mnoha případech je to jednoduché jako nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-107">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="a0cd5-108">Při vytváření vazby ke zdroji dat, který obsahuje více seznamů nebo tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> vlastnost na řetězec, který určuje seznam nebo tabulku, na které se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-108">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="a0cd5-109"><xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže se vytvoří vazba na instance tříd popsané v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="a0cd5-109">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="a0cd5-110">Libovolná třída, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-110">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="a0cd5-111">Libovolná třída, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, například <xref:System.Data.DataTable> třídy a <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="a0cd5-111">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="a0cd5-112">Libovolná třída, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, jako je například <xref:System.ComponentModel.BindingList%601> Třída.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-112">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="a0cd5-113">Libovolná třída, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, jako je například <xref:System.Windows.Forms.BindingSource> Třída.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-113">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="a0cd5-114"><xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje datovou vazbu na veřejné vlastnosti objektů vrácených těmito rozhraními nebo na kolekci vlastností vrácenou <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraním, pokud jsou implementovány u vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-114">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="a0cd5-115">Obvykle budete navazovat vazby na <xref:System.Windows.Forms.BindingSource> komponentu a navazovat <xref:System.Windows.Forms.BindingSource> komponentu na jiný zdroj dat nebo ji naplnit obchodními objekty.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-115">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="a0cd5-116">Tato <xref:System.Windows.Forms.BindingSource> součást je preferovaným zdrojem dat, protože může vytvořit vazbu na širokou škálu zdrojů dat a může automaticky vyřešit mnoho problémů s vazbami dat.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-116">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="a0cd5-117">Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="a0cd5-117">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="a0cd5-118"><xref:System.Windows.Forms.DataGridView>Ovládací prvek lze také použít v *nevázaném* režimu bez základního úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-118">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="a0cd5-119">Příklad kódu, který používá nevázaný <xref:System.Windows.Forms.DataGridView> ovládací prvek, naleznete v tématu [Návod: Vytvoření nevázaného ovládacího prvku DataGridView model Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a0cd5-119">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="a0cd5-120"><xref:System.Windows.Forms.DataGridView>Ovládací prvek je vysoce konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí pro přizpůsobení jeho vzhledu a chování.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-120">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="a0cd5-121">Pokud chcete, aby aplikace model Windows Forms zobrazovala tabulková data, zvažte použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku před ostatními (například <xref:System.Windows.Forms.DataGrid> ).</span><span class="sxs-lookup"><span data-stu-id="a0cd5-121">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="a0cd5-122">Pokud zobrazujete malou mřížku hodnot jen pro čtení, nebo pokud pro uživatele povolíte úpravu tabulky s miliony záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne snadno programovatelné řešení paměti, které je efektivní.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-122">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0cd5-123">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a0cd5-123">In This Section</span></span>  
 [<span data-ttu-id="a0cd5-124">Souhrn technologie ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-124">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="a0cd5-125">Shrnuje <xref:System.Windows.Forms.DataGridView> Koncepty řízení a použití souvisejících tříd.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-125">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="a0cd5-126">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-126">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="a0cd5-127">Popisuje architekturu <xref:System.Windows.Forms.DataGridView> ovládacího prvku, která vysvětluje jeho hierarchii typů a strukturu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-127">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="a0cd5-128">Scénáře ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-128">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="a0cd5-129">V této části najdete popis nejběžnějších scénářů, ve kterých <xref:System.Windows.Forms.DataGridView> se používají ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-129">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="a0cd5-130">Adresář kódu ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-130">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="a0cd5-131">Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-131">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="a0cd5-132">Tyto příklady jsou zařazeny do kategorií podle typu úkolu.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-132">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0cd5-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a0cd5-133">Related Sections</span></span>  
 [<span data-ttu-id="a0cd5-134">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-134">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a0cd5-135">Popisuje typy sloupců v <xref:System.Windows.Forms.DataGridView> ovládacím prvku model Windows Forms, které slouží k zobrazení informací a umožňují uživatelům upravovat nebo přidávat informace.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-135">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="a0cd5-136">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-136">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a0cd5-137">Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-137">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="a0cd5-138">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-138">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a0cd5-139">Poskytuje témata, které popisují vlastní vybarvení <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozených typů buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-139">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="a0cd5-140">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-140">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a0cd5-141">Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.</span><span class="sxs-lookup"><span data-stu-id="a0cd5-141">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0cd5-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0cd5-142">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a0cd5-143">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a0cd5-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="a0cd5-144">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-144">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a0cd5-145">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a0cd5-145">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
