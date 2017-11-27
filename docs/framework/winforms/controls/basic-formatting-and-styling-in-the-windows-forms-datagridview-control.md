---
title: "Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c6ae9c4159f8f9eafd73608e4fc3f4a646c1eaa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1ab3b-102">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1ab3b-103">`DataGridView` Ovládací prvek usnadňuje definovat základní vzhledu buněk a formátování zobrazení hodnoty buněk.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="1ab3b-104">Můžete definovat vzhled a formátování styly jednotlivých buněk, buněk v určité sloupce a řádky nebo všechny buňky v ovládacím prvku nastavením vlastnosti `DataGridViewCellStyle` objekty přistupovat prostřednictvím různých `DataGridView` vlastností ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="1ab3b-105">Kromě toho můžete upravit tyto styly dynamicky založeny na faktorech, jako je například hodnotu buňky pomocí zpracování `CellFormatting` událostí.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ab3b-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1ab3b-106">In This Section</span></span>  
 [<span data-ttu-id="1ab3b-107">Postupy: Změna ohraničení a styly mřížky v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1ab3b-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="1ab3b-108">Popisuje, jak nastavit `DataGridView` vlastnosti, které definují vzhled ohraničení ovládacího prvku a řádky hranice mezi buněk.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="1ab3b-109">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-110">Popisuje `DataGridViewCellStyle` třídy a interakci vlastnosti daného typu k definování zobrazení buňky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="1ab3b-111">Postupy: nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1ab3b-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-112">Popisuje způsob použití `DataGridViewCellStyle` vlastnosti, které chcete definovat výchozí vzhledu buněk v určitých řádků a sloupců a celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="1ab3b-113">Postupy: formátování dat v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1ab3b-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-114">Popisuje způsob zobrazení hodnot v buňkách pomocí formátování `DataGridViewCellStyle` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="1ab3b-115">Postupy: nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-116">Popisuje postup použití `DefaultCellStyle` vlastnost nastavující základní zobrazit vlastnosti pro všechny buňky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="1ab3b-117">Postupy: nastavení střídavých stylů řádků pro Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1ab3b-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-118">Popisuje, jak vytvořit efekt účetní knihy v ovládacím prvku pomocí střídavých řádků, které se zobrazují jinak.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="1ab3b-119">Postupy: použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="1ab3b-120">Popisuje postup použití `RowTemplate` vlastnost pro nastavení vlastností řádků, které se použijí pro všechny řádky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ab3b-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1ab3b-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="1ab3b-122">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="1ab3b-123">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="1ab3b-124">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="1ab3b-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ab3b-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1ab3b-126">Related Sections</span></span>  
 [<span data-ttu-id="1ab3b-127">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-127">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1ab3b-128">Obsahuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="1ab3b-129">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1ab3b-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="1ab3b-130">Obsahuje témata, která popisují běžně používá vlastnosti buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="1ab3b-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab3b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ab3b-131">See Also</span></span>  
 [<span data-ttu-id="1ab3b-132">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1ab3b-132">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
