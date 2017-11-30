---
title: "Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 313867b76d569fb98b1bd5d46c658763d0020726
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="70d10-102">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="70d10-103">Tato část obsahuje témata, která ukazují různé programovací úkoly zahrnující buněk, řádků a sloupec objekty.</span><span class="sxs-lookup"><span data-stu-id="70d10-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70d10-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="70d10-104">In This Section</span></span>  
 [<span data-ttu-id="70d10-105">Postupy: Přidání ToolTips do jednotlivých buněk ve Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="70d10-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="70d10-106">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting> událost a poskytuje různé popisy tlačítek pro jednotlivé buňky.</span><span class="sxs-lookup"><span data-stu-id="70d10-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="70d10-107">Postup: provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="70d10-108">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellValueChanged> a <xref:System.Windows.Forms.DataGridView.CellStateChanged> události.</span><span class="sxs-lookup"><span data-stu-id="70d10-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="70d10-109">Postupy: manipulace s pruhy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="70d10-110">Popisuje, jak program s objekty typu <xref:System.Windows.Forms.DataGridViewBand>, což je základní typ pro řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="70d10-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="70d10-111">Postupy: manipulace s řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="70d10-112">Popisuje, jak program s objekty typu `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="70d10-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="70d10-113">Postupy: manipulace se sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="70d10-114">Popisuje, jak program s objekty typu `DataGridViewColumn`.</span><span class="sxs-lookup"><span data-stu-id="70d10-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="70d10-115">Postupy: práce se sloupci obrázků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="70d10-116">Popisuje, jak program se `DataGridViewImageColumn` třídy.</span><span class="sxs-lookup"><span data-stu-id="70d10-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70d10-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="70d10-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="70d10-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="70d10-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="70d10-119">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCell> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d10-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="70d10-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewRow> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d10-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="70d10-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumn> třídy.</span><span class="sxs-lookup"><span data-stu-id="70d10-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70d10-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="70d10-122">Related Sections</span></span>  
 [<span data-ttu-id="70d10-123">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="70d10-124">Obsahuje témata, která popisují běžně používá vlastnosti buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="70d10-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d10-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="70d10-125">See Also</span></span>  
 [<span data-ttu-id="70d10-126">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="70d10-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="70d10-127">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="70d10-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
