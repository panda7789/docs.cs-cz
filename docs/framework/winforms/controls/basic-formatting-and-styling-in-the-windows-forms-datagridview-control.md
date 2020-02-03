---
title: Základní formátování a stylování v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731994"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b52f0-102">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b52f0-103">Ovládací prvek `DataGridView` umožňuje snadno definovat základní vzhled buněk a formátování zobrazení hodnot buněk.</span><span class="sxs-lookup"><span data-stu-id="b52f0-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="b52f0-104">Můžete definovat styly vzhledu a formátování pro jednotlivé buňky, pro buňky v určitých sloupcích a řádcích nebo pro všechny buňky v ovládacím prvku nastavením vlastností objektů `DataGridViewCellStyle`, ke kterým přistupovaly prostřednictvím různých vlastností ovládacího prvku `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="b52f0-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="b52f0-105">Kromě toho můžete tyto styly dynamicky upravovat na základě faktorů, jako je hodnota buňky, pomocí zpracování události `CellFormatting`.</span><span class="sxs-lookup"><span data-stu-id="b52f0-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b52f0-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b52f0-106">In This Section</span></span>  
 [<span data-ttu-id="b52f0-107">Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="b52f0-108">Popisuje, jak nastavit vlastnosti `DataGridView` definující vzhled ohraničení ovládacího prvku a hraniční čáry mezi buňkami.</span><span class="sxs-lookup"><span data-stu-id="b52f0-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="b52f0-109">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-110">Popisuje třídu `DataGridViewCellStyle` a způsob interakce vlastností daného typu s cílem definovat způsob zobrazení buněk v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b52f0-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="b52f0-111">Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-112">Popisuje, jak pomocí vlastností `DataGridViewCellStyle` definovat výchozí vzhled buněk v konkrétních řádcích a sloupcích a v celém ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b52f0-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="b52f0-113">Postupy: Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-114">Popisuje, jak formátovat hodnoty zobrazení buňky pomocí vlastností `DataGridViewCellStyle`.</span><span class="sxs-lookup"><span data-stu-id="b52f0-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="b52f0-115">Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-116">Popisuje, jak použít vlastnost `DefaultCellStyle` k nastavení základních vlastností zobrazení pro všechny buňky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b52f0-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="b52f0-117">Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-118">Popisuje, jak vytvořit efekt v hlavní knize v ovládacím prvku pomocí střídavých řádků, které jsou zobrazeny jinak.</span><span class="sxs-lookup"><span data-stu-id="b52f0-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="b52f0-119">Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="b52f0-120">Popisuje, jak použít vlastnost `RowTemplate` k nastavení vlastností řádku, které budou použity pro všechny řádky ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b52f0-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b52f0-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="b52f0-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b52f0-122">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b52f0-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="b52f0-123">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="b52f0-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="b52f0-124">Poskytuje referenční dokumentaci pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting>.</span><span class="sxs-lookup"><span data-stu-id="b52f0-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="b52f0-125">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="b52f0-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b52f0-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b52f0-126">Related Sections</span></span>  
 [<span data-ttu-id="b52f0-127">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b52f0-128">Poskytuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozených typů buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="b52f0-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="b52f0-129">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="b52f0-130">Poskytuje témata, která popisují běžně používané vlastnosti buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="b52f0-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b52f0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b52f0-131">See also</span></span>

- [<span data-ttu-id="b52f0-132">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="b52f0-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
