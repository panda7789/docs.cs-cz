---
title: "Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c11ca487003e57a499b3ff46178350e6aad404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="22b83-102">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="22b83-103">`DataGridView` Řízení poskytuje mnoho možností pro přizpůsobení chování nastavení velikosti řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="22b83-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="22b83-104">Obvykle `DataGridView` není změna velikosti buněk podle jejich obsah.</span><span class="sxs-lookup"><span data-stu-id="22b83-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="22b83-105">Místo toho oříznutí zobrazovanou hodnotu, která je větší než buňky.</span><span class="sxs-lookup"><span data-stu-id="22b83-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="22b83-106">Pokud obsah může být zobrazena jako řetězec, zobrazí se buňky v popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="22b83-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="22b83-107">Ve výchozím nastavení můžete přetáhnout uživatelé řádků, sloupců a oddělovače záhlaví pomocí myši zobrazíte další informace.</span><span class="sxs-lookup"><span data-stu-id="22b83-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="22b83-108">Uživatelé mohou také poklepejte na příčku automaticky změní velikost přidružené řádků, sloupců nebo hlavičce vzdálené na základě tohoto obsahu.</span><span class="sxs-lookup"><span data-stu-id="22b83-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="22b83-109">`DataGridView` Ovládací prvek obsahuje vlastnosti, metod a události, které vám umožní přizpůsobit nebo vypnout všechny tyto uživatel přesměruje chování.</span><span class="sxs-lookup"><span data-stu-id="22b83-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="22b83-110">Kromě toho můžete programově změnit velikost řádky, sloupce a záhlaví podle jejich obsahu, nebo můžete nakonfigurovat, aby automatická změna velikosti sami při každé změně jejich obsah.</span><span class="sxs-lookup"><span data-stu-id="22b83-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="22b83-111">Můžete také nakonfigurovat sloupce, které chcete automaticky dělit dostupná šířka ovládacího prvku poměr stran, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="22b83-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22b83-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="22b83-112">In This Section</span></span>  
 [<span data-ttu-id="22b83-113">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="22b83-114">Popisuje možnosti pro hlavičky, nastavení velikosti řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="22b83-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="22b83-115">Také poskytuje podrobné informace o nastavení velikosti související vlastnosti a metody a popisuje běžné scénáře použití.</span><span class="sxs-lookup"><span data-stu-id="22b83-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="22b83-116">Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="22b83-117">Režim vyplnění sloupce podrobně popisuje a poskytuje ukázkový kód, který můžete experimentovat s režim vyplnění sloupce a další režimy.</span><span class="sxs-lookup"><span data-stu-id="22b83-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="22b83-118">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="22b83-119">Popisuje postup konfigurace režimů změny velikosti pro běžné účely.</span><span class="sxs-lookup"><span data-stu-id="22b83-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="22b83-120">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="22b83-121">Poskytuje ukázkový kód, který můžete experimentovat s Programová změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="22b83-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="22b83-122">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="22b83-123">Poskytuje ukázkový kód, který můžete experimentovat s režimy Automatická změna velikosti.</span><span class="sxs-lookup"><span data-stu-id="22b83-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="22b83-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="22b83-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="22b83-125">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="22b83-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b83-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="22b83-126">See Also</span></span>  
 [<span data-ttu-id="22b83-127">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="22b83-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
