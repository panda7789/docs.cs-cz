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
ms.openlocfilehash: 992bf57642c955a87cd7675e0bbe7c52131e8039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969139"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="aa841-102">DataGridView – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="aa841-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="aa841-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="aa841-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="aa841-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aa841-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="aa841-105"><xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="aa841-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="aa841-106">Vázání dat na <xref:System.Windows.Forms.DataGridView> ovládací prvek je jednoduché a intuitivní a v mnoha případech je to jednoduché jako <xref:System.Windows.Forms.DataGridView.DataSource%2A> nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa841-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="aa841-107">Při vytváření vazby ke zdroji dat, který obsahuje více seznamů nebo tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> vlastnost na řetězec, který určuje seznam nebo tabulku, na které se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="aa841-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="aa841-108"><xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže se vytvoří vazba na instance tříd popsané v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="aa841-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="aa841-109">Libovolná třída, která <xref:System.Collections.IList> implementuje rozhraní, včetně jednorozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="aa841-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="aa841-110">Libovolná třída, která <xref:System.ComponentModel.IListSource> implementuje rozhraní, například <xref:System.Data.DataTable> třídy a <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="aa841-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="aa841-111">Libovolná třída, která <xref:System.ComponentModel.IBindingList> implementuje rozhraní, jako je <xref:System.ComponentModel.BindingList%601> například třída.</span><span class="sxs-lookup"><span data-stu-id="aa841-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="aa841-112">Libovolná třída, která <xref:System.ComponentModel.IBindingListView> implementuje rozhraní, jako je <xref:System.Windows.Forms.BindingSource> například třída.</span><span class="sxs-lookup"><span data-stu-id="aa841-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="aa841-113">Ovládací prvek podporuje datovou vazbu na veřejné vlastnosti objektů vrácených těmito rozhraními nebo na kolekci vlastností vrácenou <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraním, pokud jsou implementovány u vrácených objektů. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="aa841-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="aa841-114">Obvykle budete navazovat vazby na <xref:System.Windows.Forms.BindingSource> komponentu a <xref:System.Windows.Forms.BindingSource> navazovat komponentu na jiný zdroj dat nebo ji naplnit obchodními objekty.</span><span class="sxs-lookup"><span data-stu-id="aa841-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="aa841-115">Tato <xref:System.Windows.Forms.BindingSource> součást je preferovaným zdrojem dat, protože může vytvořit vazbu na širokou škálu zdrojů dat a může automaticky vyřešit mnoho problémů s vazbami dat.</span><span class="sxs-lookup"><span data-stu-id="aa841-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="aa841-116">Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="aa841-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="aa841-117">Ovládací prvek lze také použít v nevázaném režimu bez základního úložiště dat. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="aa841-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="aa841-118">Příklad kódu, který používá nevázaný <xref:System.Windows.Forms.DataGridView> ovládací prvek, naleznete v tématu [Návod: Vytváření nevázaného ovládacího prvku](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)DataGridView model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aa841-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="aa841-119"><xref:System.Windows.Forms.DataGridView> Ovládací prvek je vysoce konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí pro přizpůsobení jeho vzhledu a chování.</span><span class="sxs-lookup"><span data-stu-id="aa841-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="aa841-120">Pokud chcete, aby aplikace model Windows Forms zobrazovala tabulková data, zvažte použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku před ostatními ( <xref:System.Windows.Forms.DataGrid>například).</span><span class="sxs-lookup"><span data-stu-id="aa841-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="aa841-121">Pokud zobrazujete malou mřížku hodnot jen pro čtení, nebo pokud pro uživatele povolíte úpravu tabulky s miliony záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne snadno programovatelné řešení paměti, které je efektivní.</span><span class="sxs-lookup"><span data-stu-id="aa841-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa841-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa841-122">In This Section</span></span>  
 [<span data-ttu-id="aa841-123">Souhrn technologie ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="aa841-124">Shrnuje koncepty <xref:System.Windows.Forms.DataGridView> řízení a použití souvisejících tříd.</span><span class="sxs-lookup"><span data-stu-id="aa841-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="aa841-125">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="aa841-126">Popisuje architekturu <xref:System.Windows.Forms.DataGridView> ovládacího prvku, která vysvětluje jeho hierarchii typů a strukturu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="aa841-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="aa841-127">Scénáře ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="aa841-128">V této části najdete popis nejběžnějších <xref:System.Windows.Forms.DataGridView> scénářů, ve kterých se používají ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="aa841-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="aa841-129">Adresář kódu ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="aa841-130">Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy.</span><span class="sxs-lookup"><span data-stu-id="aa841-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="aa841-131">Tyto příklady jsou zařazeny do kategorií podle typu úkolu.</span><span class="sxs-lookup"><span data-stu-id="aa841-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa841-132">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa841-132">Related Sections</span></span>  
 [<span data-ttu-id="aa841-133">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="aa841-134">Popisuje typy sloupců v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView> , které slouží k zobrazení informací a umožňují uživatelům upravovat nebo přidávat informace.</span><span class="sxs-lookup"><span data-stu-id="aa841-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="aa841-135">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="aa841-136">Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="aa841-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="aa841-137">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="aa841-138">Poskytuje témata, které popisují vlastní <xref:System.Windows.Forms.DataGridView> vybarvení buněk a řádků a vytváření odvozených typů buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="aa841-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="aa841-139">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="aa841-140">Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.</span><span class="sxs-lookup"><span data-stu-id="aa841-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa841-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa841-141">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="aa841-142">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="aa841-143">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="aa841-144">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="aa841-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
