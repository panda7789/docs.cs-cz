---
title: Změna velikosti sloupců a řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742409"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="18057-102">Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="18057-103">Ovládací prvek `DataGridView` poskytuje mnoho možností přizpůsobení chování při změně velikosti sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="18057-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="18057-104">Obvykle `DataGridView` buňky nemění velikost na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="18057-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="18057-105">Místo toho vystřihnout libovolnou zobrazovanou hodnotu, která je větší než buňka.</span><span class="sxs-lookup"><span data-stu-id="18057-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="18057-106">Pokud se obsah může zobrazit jako řetězec, buňka ho zobrazí v popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="18057-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="18057-107">Ve výchozím nastavení mohou uživatelé zobrazit další informace přetažením řádku, sloupce a oddělovače záhlaví pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="18057-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="18057-108">Uživatelé také mohou dvakrát kliknout na oddělovač, aby automaticky změnil velikost přidruženého řádku, sloupce nebo záhlaví na základě jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="18057-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="18057-109">Ovládací prvek `DataGridView` poskytuje vlastnosti, metody a události, které vám umožní přizpůsobit nebo zakázat všechna tato chování zaměřené na uživatele.</span><span class="sxs-lookup"><span data-stu-id="18057-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="18057-110">Kromě toho můžete programově měnit velikost řádků, sloupců a záhlaví, které odpovídají jejich obsahu, nebo je můžete nakonfigurovat tak, aby se při změně jejich obsahu automaticky změnila velikost.</span><span class="sxs-lookup"><span data-stu-id="18057-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="18057-111">Můžete také nakonfigurovat sloupce pro automatické rozdělení dostupné šířky ovládacího prvku v poměrech, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="18057-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18057-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18057-112">In This Section</span></span>  
 [<span data-ttu-id="18057-113">Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="18057-114">Popisuje možnosti pro změnu velikosti řádků, sloupců a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="18057-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="18057-115">Poskytuje také podrobné informace o vlastnostech a metodách souvisejících s určením velikosti a popisuje běžné scénáře použití.</span><span class="sxs-lookup"><span data-stu-id="18057-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="18057-116">Režim vyplnění sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="18057-117">Popisuje režim výplně sloupce podrobně a poskytuje ukázku kódu, který můžete použít k experimentování s režimem výplně sloupců a dalšími režimy.</span><span class="sxs-lookup"><span data-stu-id="18057-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="18057-118">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="18057-119">V této části najdete popis postupu konfigurace režimů změny velikosti pro běžné účely.</span><span class="sxs-lookup"><span data-stu-id="18057-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="18057-120">Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="18057-121">Poskytuje ukázku kódu, který můžete použít k experimentování s programovou změnou velikosti.</span><span class="sxs-lookup"><span data-stu-id="18057-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="18057-122">Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="18057-123">Poskytuje ukázku kódu, který můžete použít k experimentování s automatickými režimy velikosti.</span><span class="sxs-lookup"><span data-stu-id="18057-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="18057-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="18057-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="18057-125">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="18057-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18057-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18057-126">See also</span></span>

- [<span data-ttu-id="18057-127">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="18057-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
