---
title: DataGridView – ovládací prvek
description: Naučte se používat `DataGridView` ovládací prvek k zobrazení zobrazení s malým množstvím dat jen pro čtení, nebo ke změně velikosti pro zobrazení upravitelných zobrazení velmi rozsáhlých datových sad.
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
ms.openlocfilehash: f9a45e8be7975697ca5c0d019c6bc4119f562aea
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325900"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="27141-103">DataGridView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="27141-103">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="27141-104">`DataGridView`Ovládací prvek poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu.</span><span class="sxs-lookup"><span data-stu-id="27141-104">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="27141-105">Ovládací prvek můžete použít `DataGridView` k zobrazení zobrazení s malým množstvím dat jen pro čtení, nebo můžete škálovat a zobrazit upravitelná zobrazení velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="27141-105">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="27141-106">Ovládací prvek můžete roztáhnout `DataGridView` mnoha způsoby, abyste mohli vytvářet vlastní chování do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="27141-106">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="27141-107">Můžete například programově zadat vlastní algoritmy řazení a můžete vytvořit vlastní typy buněk.</span><span class="sxs-lookup"><span data-stu-id="27141-107">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="27141-108">Vzhled ovládacího prvku lze snadno přizpůsobit výběrem `DataGridView` z několika vlastností.</span><span class="sxs-lookup"><span data-stu-id="27141-108">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="27141-109">Jako zdroj dat lze použít mnoho typů úložišť dat, nebo `DataGridView` ovládací prvek může fungovat bez vazby na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="27141-109">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="27141-110">Témata v této části popisují koncepty a techniky, které můžete použít k vytváření funkcí v `DataGridView` aplikacích.</span><span class="sxs-lookup"><span data-stu-id="27141-110">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27141-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27141-111">In This Section</span></span>  
 [<span data-ttu-id="27141-112">DataGridView – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="27141-112">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="27141-113">Poskytuje témata, která popisují architekturu a základní koncepty `DataGridView` ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27141-113">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="27141-114">Výchozí funkce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-114">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-115">Popisuje výchozí vzhled a chování ovládacího prvku model Windows Forms, `DataGridView` když je svázán se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="27141-115">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="27141-116">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-116">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-117">Popisuje typy sloupců v `DataGridView` ovládacím prvku model Windows Forms, které slouží k zobrazení dat a umožňují uživatelům upravovat nebo přidávat data.</span><span class="sxs-lookup"><span data-stu-id="27141-117">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="27141-118">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="27141-119">Poskytuje témata, která popisují běžně používané vlastnosti buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="27141-119">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="27141-120">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-121">Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.</span><span class="sxs-lookup"><span data-stu-id="27141-121">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="27141-122">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-123">Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="27141-123">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="27141-124">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-124">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-125">Poskytuje témata, která popisují, jak lze velikost řádků a sloupců automaticky upravit tak, aby odpovídala obsahu buňky nebo aby odpovídala dostupné šířce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="27141-125">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="27141-126">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-126">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-127">Obsahuje témata, která popisují funkce řazení v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="27141-127">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="27141-128">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-128">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-129">Poskytuje témata, která popisují, jak změnit způsob, jakým uživatelé přidávají a upravují data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="27141-129">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="27141-130">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-130">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-131">Obsahuje témata, která popisují funkce výběru buněk, řádků a sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="27141-131">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="27141-132">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-132">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="27141-133">Poskytuje témata, která popisují, jak programovat s objekty buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="27141-133">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="27141-134">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-134">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-135">Poskytuje témata, které popisují vlastní vybarvení `DataGridView` buněk a řádků a vytváření odvozených typů buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="27141-135">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="27141-136">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-136">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-137">Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.</span><span class="sxs-lookup"><span data-stu-id="27141-137">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="27141-138">Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="27141-138">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="27141-139">Popisuje, jak uživatelé mohou pracovat s `DataGridView` ovládacím prvkem prostřednictvím klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="27141-139">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="27141-140">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="27141-140">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="27141-141">Popisuje, jak se `DataGridView` ovládací prvek zlepšuje a nahrazuje <xref:System.Windows.Forms.DataGrid> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="27141-141">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="27141-142">Viz také téma [použití návrháře s ovládacím prvkem model Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="27141-142">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27141-143">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="27141-143">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="27141-144">Poskytuje referenční dokumentaci k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="27141-144">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="27141-145">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponentu.</span><span class="sxs-lookup"><span data-stu-id="27141-145">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="27141-146"><xref:System.Windows.Forms.DataGridView>Ovládací prvek a <xref:System.Windows.Forms.BindingSource> součást jsou navržené tak, aby úzce spolupracovaly.</span><span class="sxs-lookup"><span data-stu-id="27141-146">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27141-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="27141-147">See also</span></span>

- [<span data-ttu-id="27141-148">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27141-148">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
