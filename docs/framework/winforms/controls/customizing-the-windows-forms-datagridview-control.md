---
title: "Přizpůsobení ovládacího prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d1246a8052af19057f7aa9d6729e34203177f8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="79efa-102">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="79efa-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="79efa-103">`DataGridView` Řízení nabízí několik vlastností, které můžete upravit vzhled a chování základní (vzhled a chování) jeho buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="79efa-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="79efa-104">Pokud máte speciální požadavky nad rámec možností <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, ale můžete také implementovat kreslení pro ovládací prvek vlastníka nebo rozšířit možnosti tak, že vytvoříte vlastní buněk, sloupce a řádky.</span><span class="sxs-lookup"><span data-stu-id="79efa-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="79efa-105">Chcete-li malovat buněk a řádky, sami, může zpracovávat různé `DataGridView` Malování události.</span><span class="sxs-lookup"><span data-stu-id="79efa-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="79efa-106">Chcete-li upravit stávající funkce nebo přinášejí nové funkce, můžete vytvořit vlastní typy odvozené z existující `DataGridViewCell`, `DataGridViewColumn`, a `DataGridViewRow` typy.</span><span class="sxs-lookup"><span data-stu-id="79efa-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="79efa-107">Můžete zadat také nové možnosti úprav vytvořením odvozené typy, které zobrazení ovládacího prvku dle vlastního výběru, když je buňku v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="79efa-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79efa-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="79efa-108">In This Section</span></span>  
 [<span data-ttu-id="79efa-109">Postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="79efa-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="79efa-110">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellPainting> událostí k vyplnění buněk ručně.</span><span class="sxs-lookup"><span data-stu-id="79efa-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="79efa-111">Postupy: přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="79efa-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="79efa-112">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> události k vykreslení řádky s vlastní, barevného přechodu pozadí nebo obsahu, který zahrnuje několik sloupců.</span><span class="sxs-lookup"><span data-stu-id="79efa-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="79efa-113">Postupy: přizpůsobení buněk a sloupců v systému Windows Forms DataGridView – ovládací prvek rozšířením jeho chování a vzhledu</span><span class="sxs-lookup"><span data-stu-id="79efa-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="79efa-114">Popisuje, jak vytvořit vlastní typy odvozené od `DataGridViewCell` a `DataGridViewColumn` Chcete-li zvýraznění buněk při umístění ukazatele myši na ně.</span><span class="sxs-lookup"><span data-stu-id="79efa-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="79efa-115">Postupy: zákaz tlačítek ve sloupci tlačítek v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="79efa-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="79efa-116">Popisuje, jak vytvořit vlastní typy odvozené od <xref:System.Windows.Forms.DataGridViewButtonCell> a <xref:System.Windows.Forms.DataGridViewButtonColumn> aby bylo možné zobrazit zakázané tlačítek ve sloupci tlačítek.</span><span class="sxs-lookup"><span data-stu-id="79efa-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="79efa-117">Postupy: umisťování ovládacích prvků ve Windows Forms DataGridView buněk</span><span class="sxs-lookup"><span data-stu-id="79efa-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="79efa-118">Popisuje, jak implementovat `IDataGridViewEditingControl` rozhraní a vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn` aby bylo možné zobrazit <xref:System.Windows.Forms.DateTimePicker> řídit, kdy buňku je v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="79efa-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79efa-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="79efa-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="79efa-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="79efa-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="79efa-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewCell> třídy.</span><span class="sxs-lookup"><span data-stu-id="79efa-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="79efa-122">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewRow> třídy.</span><span class="sxs-lookup"><span data-stu-id="79efa-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="79efa-123">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumn> třídy.</span><span class="sxs-lookup"><span data-stu-id="79efa-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="79efa-124">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.IDataGridViewEditingControl> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="79efa-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79efa-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="79efa-125">Related Sections</span></span>  
 [<span data-ttu-id="79efa-126">Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="79efa-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="79efa-127">Obsahuje témata, která popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.</span><span class="sxs-lookup"><span data-stu-id="79efa-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79efa-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="79efa-128">See Also</span></span>  
 [<span data-ttu-id="79efa-129">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="79efa-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="79efa-130">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="79efa-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
