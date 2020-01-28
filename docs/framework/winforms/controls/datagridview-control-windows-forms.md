---
title: DataGridView – ovládací prvek
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
ms.openlocfilehash: fc40c0f08c0c11fa9acc94ce12caab8766658f1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746946"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="92725-102">DataGridView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="92725-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="92725-103">Ovládací prvek `DataGridView` poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="92725-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="92725-104">Ovládací prvek `DataGridView` můžete použít k zobrazení zobrazení s malým množstvím dat jen pro čtení, nebo můžete škálovat a zobrazit upravitelná zobrazení velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="92725-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="92725-105">Ovládací prvek `DataGridView` můžete v různých způsobech, jak vytvořit vlastní chování, do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="92725-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="92725-106">Můžete například programově zadat vlastní algoritmy řazení a můžete vytvořit vlastní typy buněk.</span><span class="sxs-lookup"><span data-stu-id="92725-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="92725-107">Vzhled ovládacího prvku `DataGridView` lze snadno přizpůsobit výběrem z několika vlastností.</span><span class="sxs-lookup"><span data-stu-id="92725-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="92725-108">Jako zdroj dat lze použít mnoho typů úložišť dat, nebo ovládací prvek `DataGridView` může pracovat bez vazby na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="92725-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="92725-109">Témata v této části popisují koncepty a techniky, které můžete použít k sestavení `DataGridView`ch funkcí do aplikací.</span><span class="sxs-lookup"><span data-stu-id="92725-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92725-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="92725-110">In This Section</span></span>  
 [<span data-ttu-id="92725-111">Přehled ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-111">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="92725-112">Poskytuje témata popisující architekturu a základní koncepty ovládacího prvku model Windows Forms `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="92725-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="92725-113">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-114">Popisuje výchozí vzhled a chování ovládacího prvku model Windows Forms `DataGridView`, když je svázán se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="92725-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="92725-115">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-115">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-116">Popisuje typy sloupců v ovládacím prvku model Windows Forms `DataGridView`, který slouží k zobrazení dat a umožňuje uživatelům upravovat nebo přidávat data.</span><span class="sxs-lookup"><span data-stu-id="92725-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="92725-117">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="92725-118">Poskytuje témata, která popisují běžně používané vlastnosti buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="92725-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="92725-119">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-120">Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.</span><span class="sxs-lookup"><span data-stu-id="92725-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="92725-121">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-122">Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="92725-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="92725-123">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-124">Poskytuje témata, která popisují, jak lze velikost řádků a sloupců automaticky upravit tak, aby odpovídala obsahu buňky nebo aby odpovídala dostupné šířce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="92725-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="92725-125">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-126">Obsahuje témata, která popisují funkce řazení v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="92725-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="92725-127">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-127">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-128">Poskytuje témata, která popisují, jak změnit způsob, jakým uživatelé přidávají a upravují data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="92725-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="92725-129">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-130">Obsahuje témata, která popisují funkce výběru buněk, řádků a sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="92725-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="92725-131">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="92725-132">Poskytuje témata, která popisují, jak programovat s objekty buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="92725-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="92725-133">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-133">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-134">Poskytuje témata, která popisují vlastní Malování `DataGridView` buňky a řádky a vytváření odvozených typů buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="92725-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="92725-135">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-136">Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.</span><span class="sxs-lookup"><span data-stu-id="92725-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="92725-137">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="92725-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92725-138">Popisuje, jak mohou uživatelé pracovat s ovládacím prvkem `DataGridView` prostřednictvím klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="92725-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="92725-139">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="92725-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="92725-140">Popisuje způsob, jakým `DataGridView` ovládací prvek vylepšuje a nahrazuje ovládací prvek <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="92725-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="92725-141">Viz také téma [použití návrháře s ovládacím prvkem model Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="92725-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="92725-142">Odkaz</span><span class="sxs-lookup"><span data-stu-id="92725-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="92725-143">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="92725-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="92725-144">Poskytuje referenční dokumentaci pro součást <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="92725-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="92725-145">Ovládací prvek <xref:System.Windows.Forms.DataGridView> a komponenta <xref:System.Windows.Forms.BindingSource> jsou navržené tak, aby úzce spolupracovaly.</span><span class="sxs-lookup"><span data-stu-id="92725-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92725-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92725-146">See also</span></span>

- [<span data-ttu-id="92725-147">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="92725-147">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
