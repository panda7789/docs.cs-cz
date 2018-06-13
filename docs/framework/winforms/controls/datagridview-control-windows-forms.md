---
title: DataGridView – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: 3c642a2a0eccc5a2b08cee71ca719515b115b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529922"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="013c5-102">DataGridView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="013c5-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="013c5-103">`DataGridView` Řízení poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky.</span><span class="sxs-lookup"><span data-stu-id="013c5-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="013c5-104">Můžete použít `DataGridView` řízení zobrazíte jen pro čtení zobrazení malé množství dat nebo je možné škálovat, aby bylo zřejmé, upravitelných zobrazeních velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="013c5-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="013c5-105">Můžete rozšířit `DataGridView` řízení různými způsoby, jak vytvořit vlastní chování do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="013c5-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="013c5-106">Například můžete programově zadat vlastní řazení algoritmy a můžete vytvořit vlastní typy buněk.</span><span class="sxs-lookup"><span data-stu-id="013c5-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="013c5-107">Můžete snadno přizpůsobit vzhled `DataGridView` řízení můžete volit mezi několik vlastností.</span><span class="sxs-lookup"><span data-stu-id="013c5-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="013c5-108">Mnoho typů úložišť dat lze použít jako zdroj dat nebo `DataGridView` řízení můžete pracovat s žádný zdroj dat, který je vázaný na ni.</span><span class="sxs-lookup"><span data-stu-id="013c5-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="013c5-109">Témata v této části popisují koncepty a techniky, které můžete použít k vytvoření `DataGridView` funkce do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="013c5-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="013c5-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="013c5-110">In This Section</span></span>  
 [<span data-ttu-id="013c5-111">Přehled ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="013c5-112">Obsahuje témata, která popisují architekturu a základní koncepty Windows Forms `DataGridView` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="013c5-113">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-114">Popisuje výchozí vzhled a chování Windows Forms `DataGridView` řídit, kdy je vázán na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="013c5-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="013c5-115">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-116">Popisuje typy sloupců v modelu Windows Forms `DataGridView` ovládací prvek použitý k zobrazení dat a povolit uživatelům změnit nebo přidat data.</span><span class="sxs-lookup"><span data-stu-id="013c5-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="013c5-117">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="013c5-118">Obsahuje témata, která popisují běžně používané vlastnosti buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="013c5-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="013c5-119">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-120">Obsahuje témata, která popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.</span><span class="sxs-lookup"><span data-stu-id="013c5-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="013c5-121">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-122">Obsahuje témata, která popisují, jak buď ručně, nebo z externího zdroje dat naplnit ovládací prvek s daty.</span><span class="sxs-lookup"><span data-stu-id="013c5-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="013c5-123">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-124">Obsahuje témata, která popisují, jak velikosti řádků a sloupců lze upravit automaticky podle obsahu buňky nebo podle dostupné šířky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="013c5-125">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-126">Obsahuje témata, která popisují řazení funkce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="013c5-127">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-128">Obsahuje témata, která popisují, jak změnit způsob uživatele, přidání a změna dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="013c5-129">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-130">Obsahuje témata, která popisují funkce Výběr buněk, řádků a sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="013c5-131">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="013c5-132">Obsahuje témata, která popisují, jak programovat s buněk, řádků a sloupec objekty.</span><span class="sxs-lookup"><span data-stu-id="013c5-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="013c5-133">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-134">Obsahuje témata, která popisují vlastní Malování `DataGridView` buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.</span><span class="sxs-lookup"><span data-stu-id="013c5-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="013c5-135">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-136">Obsahuje témata, která popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkými objemy dat.</span><span class="sxs-lookup"><span data-stu-id="013c5-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="013c5-137">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="013c5-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="013c5-138">Popisuje, jak mohou uživatelé komunikovat s `DataGridView` řízení prostřednictvím klávesnici a myš.</span><span class="sxs-lookup"><span data-stu-id="013c5-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="013c5-139">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="013c5-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="013c5-140">Popisuje, jak `DataGridView` řízení zlepšuje při a nahradí <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="013c5-141">Viz také [s ovládacím prvkem Windows Forms DataGridView pomocí návrháře](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="013c5-141">Also see [Using the Designer with the Windows Forms DataGridView Control](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="013c5-142">Odkaz</span><span class="sxs-lookup"><span data-stu-id="013c5-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="013c5-143">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="013c5-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="013c5-144">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="013c5-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="013c5-145"><xref:System.Windows.Forms.DataGridView> Řízení a <xref:System.Windows.Forms.BindingSource> součást jsou navrženy pro práci úzce spolupracují.</span><span class="sxs-lookup"><span data-stu-id="013c5-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013c5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="013c5-146">See Also</span></span>  
 [<span data-ttu-id="013c5-147">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="013c5-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
