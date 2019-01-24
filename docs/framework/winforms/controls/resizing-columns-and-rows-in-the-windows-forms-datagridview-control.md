---
title: Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e2be90a1367bdcbb5b9c6441a407e3e23e5204c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711246"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f1805-102">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f1805-103">`DataGridView` Řízení poskytuje mnoho možností pro přizpůsobení chování nastavení velikosti řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="f1805-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="f1805-104">Obvykle `DataGridView` buněk nelze změnit velikost na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="f1805-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="f1805-105">Místo toho galerie zobrazit hodnotu, která je větší než buňku.</span><span class="sxs-lookup"><span data-stu-id="f1805-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="f1805-106">Pokud obsah může být zobrazena jako řetězec, zobrazí se buňku v popisku.</span><span class="sxs-lookup"><span data-stu-id="f1805-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="f1805-107">Ve výchozím nastavení můžete přetáhnout uživatelé řádků, sloupců a oddělovače záhlaví pomocí myši zobrazíte další informace.</span><span class="sxs-lookup"><span data-stu-id="f1805-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="f1805-108">Uživatele můžete také dvakrát kliknout na oddělovač automaticky změní velikost přidružené řádek, sloupec nebo záhlaví obsluhy vzdálené správy na základě jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="f1805-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="f1805-109">`DataGridView` Ovládací prvek obsahuje vlastnosti, metody a události, které vám umožní přizpůsobit nebo vypnout všechny z těchto projevů se uživatel přesměruje.</span><span class="sxs-lookup"><span data-stu-id="f1805-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="f1805-110">Kromě toho můžete programově změnit velikost řádky, sloupce a záhlaví podle jejich obsahu, nebo můžete nakonfigurovat, je automaticky změní velikost sami při každé změně jejich obsah.</span><span class="sxs-lookup"><span data-stu-id="f1805-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="f1805-111">Můžete také nakonfigurovat sloupce, které chcete automaticky dělit dostupná šířka ovládacího prvku v proporcích, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="f1805-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1805-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f1805-112">In This Section</span></span>  
 [<span data-ttu-id="f1805-113">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f1805-114">Popisuje možnosti pro nastavení velikosti řádků, sloupců a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f1805-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="f1805-115">Také poskytuje podrobné informace o určení velikosti související vlastnosti a metody a popisuje běžné scénáře použití.</span><span class="sxs-lookup"><span data-stu-id="f1805-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="f1805-116">Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f1805-117">Režim vyplnění sloupce podrobně popisuje a obsahuje ukázky kódu, který vám pomůže experimentovat s režim vyplnění sloupce a jiné režimy.</span><span class="sxs-lookup"><span data-stu-id="f1805-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="f1805-118">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="f1805-119">Popisuje postup konfigurace režimů změny velikosti pro běžné účely.</span><span class="sxs-lookup"><span data-stu-id="f1805-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="f1805-120">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="f1805-121">Obsahuje ukázku kódu, který vám pomůže experimentovat s Programová změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="f1805-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="f1805-122">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="f1805-123">Obsahuje ukázku kódu, který vám pomůže experimentovat s režim automatické velikosti.</span><span class="sxs-lookup"><span data-stu-id="f1805-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1805-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f1805-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="f1805-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f1805-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1805-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1805-126">See also</span></span>
- [<span data-ttu-id="f1805-127">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="f1805-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
