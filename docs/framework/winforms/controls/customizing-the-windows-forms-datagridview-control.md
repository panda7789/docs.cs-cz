---
title: Přizpůsobení ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744022"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="35672-102">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="35672-103">Ovládací prvek `DataGridView` poskytuje několik vlastností, které lze použít k úpravě vzhledu a základního chování (vzhled a chování) jeho buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="35672-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="35672-104">Pokud máte zvláštní potřeby, které překračují možnosti <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, můžete také implementovat vykreslování vlastníka pro ovládací prvek nebo roztáhnout jeho funkce vytvořením vlastních buněk, sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="35672-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="35672-105">Chcete-li malovat buňky a řádky sami, můžete zpracovat různé události Malování `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="35672-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="35672-106">Chcete-li upravit stávající funkce nebo poskytnout nové funkce, můžete vytvořit vlastní typy odvozené z existujících `DataGridViewCell`, `DataGridViewColumn`a typů `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="35672-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="35672-107">Můžete také poskytnout nové možnosti úprav vytvořením odvozených typů, které zobrazí ovládací prvek výběru, pokud je buňka v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="35672-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35672-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="35672-108">In This Section</span></span>  
 [<span data-ttu-id="35672-109">Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="35672-110">Popisuje, jak zpracovat událost <xref:System.Windows.Forms.DataGridView.CellPainting>, aby bylo možné buňky vykreslit ručně.</span><span class="sxs-lookup"><span data-stu-id="35672-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="35672-111">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="35672-112">Popisuje, jak zpracovávat události <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint>, aby bylo možné malovat řádky s vlastním pozadím a obsahem přechodu, které jsou rozloženy do více sloupců.</span><span class="sxs-lookup"><span data-stu-id="35672-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="35672-113">Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu</span><span class="sxs-lookup"><span data-stu-id="35672-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="35672-114">Popisuje, jak vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn`, aby bylo možné zvýraznit buňky, když se na ně ukazatel myši nachází.</span><span class="sxs-lookup"><span data-stu-id="35672-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="35672-115">Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="35672-116">Popisuje, jak vytvořit vlastní typy odvozené z <xref:System.Windows.Forms.DataGridViewButtonCell> a <xref:System.Windows.Forms.DataGridViewButtonColumn>, aby se zobrazila zakázaná tlačítka ve sloupci tlačítka.</span><span class="sxs-lookup"><span data-stu-id="35672-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="35672-117">Postupy: Hostování ovládacích prvků v buňkách Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="35672-118">Popisuje, jak implementovat rozhraní `IDataGridViewEditingControl` a vytvořit vlastní typy odvozené z `DataGridViewCell` a `DataGridViewColumn`, aby bylo možné zobrazit ovládací prvek <xref:System.Windows.Forms.DateTimePicker>, pokud je buňka v režimu úprav.</span><span class="sxs-lookup"><span data-stu-id="35672-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35672-119">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="35672-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="35672-120">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="35672-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="35672-121">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="35672-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="35672-122">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="35672-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="35672-123">Poskytuje referenční dokumentaci pro třídu <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="35672-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="35672-124">Poskytuje referenční dokumentaci pro rozhraní <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="35672-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35672-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="35672-125">Related Sections</span></span>  
 [<span data-ttu-id="35672-126">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="35672-127">Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.</span><span class="sxs-lookup"><span data-stu-id="35672-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35672-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="35672-128">See also</span></span>

- [<span data-ttu-id="35672-129">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="35672-130">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="35672-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
