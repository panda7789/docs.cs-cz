---
title: Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 3d185b93f1e040ae320afbfd3e2b010bbf9ca624
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707076"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="527f4-102">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="527f4-103">`DataGridView` Ovládací prvek umožňuje snadno definovat základního vzhledu buněk a formátování zobrazení hodnot v buňkách.</span><span class="sxs-lookup"><span data-stu-id="527f4-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="527f4-104">Můžete definovat vzhled a formátování styly pro jednotlivé buňky, buněk v určité sloupce a řádky nebo všechny buňky v ovládacím prvku nastavením vlastnosti `DataGridViewCellStyle` objekty přístupné na základě různých `DataGridView` vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="527f4-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="527f4-105">Kromě toho můžete upravit tyto styly dynamicky na základě faktorů, jako je například hodnota buňky pomocí manipulace `CellFormatting` událostí.</span><span class="sxs-lookup"><span data-stu-id="527f4-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="527f4-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="527f4-106">In This Section</span></span>  
 [<span data-ttu-id="527f4-107">Postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="527f4-108">Popisuje, jak nastavit `DataGridView` vlastnosti, které definují vzhled ohraničení ovládacího prvku a hranice čar mezi buňkami.</span><span class="sxs-lookup"><span data-stu-id="527f4-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="527f4-109">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-110">Popisuje `DataGridViewCellStyle` třídy a interakci vlastnosti tohoto typu pro definování zobrazení buňky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="527f4-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="527f4-111">Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-112">Popisuje způsob použití `DataGridViewCellStyle` vlastnosti, které chcete definovat výchozí vzhledu buněk v konkrétní řádky a sloupce a celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="527f4-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="527f4-113">Postupy: Formát dat v Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-114">Popisuje, jak formátovat zobrazované hodnoty buňky pomocí `DataGridViewCellStyle` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="527f4-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="527f4-115">Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-116">Popisuje způsob použití `DefaultCellStyle` vlastnosti chcete nastavit základní zobrazit vlastnosti pro všechny buňky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="527f4-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="527f4-117">Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-118">Popisuje postup vytvoření účetní knihy efektu v ovládacím prvku pomocí střídavé řádky, které se zobrazují jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="527f4-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="527f4-119">Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="527f4-120">Popisuje způsob použití `RowTemplate` vlastnosti chcete nastavit vlastnosti řádku, které se použijí pro všechny řádky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="527f4-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="527f4-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="527f4-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="527f4-122">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="527f4-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="527f4-123">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="527f4-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="527f4-124">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.</span><span class="sxs-lookup"><span data-stu-id="527f4-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="527f4-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="527f4-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="527f4-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="527f4-126">Related Sections</span></span>  
 [<span data-ttu-id="527f4-127">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="527f4-128">Obsahuje témata, které popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozené buňky, sloupce a typy řádků.</span><span class="sxs-lookup"><span data-stu-id="527f4-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="527f4-129">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="527f4-130">Obsahuje témata, která popisují běžně používané vlastnosti buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="527f4-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527f4-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="527f4-131">See also</span></span>
- [<span data-ttu-id="527f4-132">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="527f4-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
