---
title: "Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fbdb3778959d1691200cde49e485d8a63c6e645
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="9436d-102">Přehled ovládacích prvků HScrollBar a VScrollBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9436d-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="9436d-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> používají se ovládací prvky pro navigaci v seznamu položek nebo velké množství informací posouváním buď vodorovně nebo svisle v rámci aplikace nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9436d-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="9436d-104">Posuvníky jsou běžné element rozhraní systému Windows, proto <xref:System.Windows.Forms.ScrollBar> ovládací prvek se často používá s ovládacími prvky, které není odvozena od <xref:System.Windows.Forms.ScrollableControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="9436d-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="9436d-105">Podobně se celá řada vývojářů rozhodnete začlenit <xref:System.Windows.Forms.ScrollBar> řízení při vytváření vlastní uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9436d-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="9436d-106"><xref:System.Windows.Forms.HScrollBar> (Vodorovně) a <xref:System.Windows.Forms.VScrollBar> (svislé) ovládacích prvků fungovat nezávisle z jiných ovládacích prvků a mít vlastní sadu událostí, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="9436d-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="9436d-107"><xref:System.Windows.Forms.ScrollBar>ovládací prvky nejsou stejná jako integrované posuvníky, které jsou připojené k textová pole, seznamy, pole se seznamem nebo formulářů MDI ( <xref:System.Windows.Forms.TextBox> má ovládací prvek <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti chcete zobrazit nebo skrýt posuvníky, které jsou připojené k ovládacímu prvku).</span><span class="sxs-lookup"><span data-stu-id="9436d-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="9436d-108"><xref:System.Windows.Forms.ScrollBar> Řídí použití <xref:System.Windows.Forms.ScrollBar.Scroll> události k monitorování přesun od jezdce (někdy označované jako úchytu) podél posuvníku.</span><span class="sxs-lookup"><span data-stu-id="9436d-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="9436d-109">Pomocí <xref:System.Windows.Forms.ScrollBar.Scroll> událostí poskytuje přístup k hodnotě panelu přejděte, jako je právě přetáhli.</span><span class="sxs-lookup"><span data-stu-id="9436d-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="9436d-110">Value – vlastnost</span><span class="sxs-lookup"><span data-stu-id="9436d-110">Value Property</span></span>  
 <span data-ttu-id="9436d-111"><xref:System.Windows.Forms.ScrollBar.Value%2A> Vlastnost (která je ve výchozím nastavení, 0) je `integer` hodnotu odpovídající pozice jezdce posuvníku.</span><span class="sxs-lookup"><span data-stu-id="9436d-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="9436d-112">Když na pozici posunutí pole na minimální hodnotu, přesune na pozici nejvíce vlevo (pro vodorovné posuvníky) nebo nejvyšší pozici (pro svislé posuvníky).</span><span class="sxs-lookup"><span data-stu-id="9436d-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="9436d-113">Když posouvací políčko je na maximální hodnotu, posuňte pole přesun do nejvíce vpravo nebo dolní pozici.</span><span class="sxs-lookup"><span data-stu-id="9436d-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="9436d-114">Podobně hodnotu uprostřed mezi dolní a horní části rozsahu, umístí úvodní hrany posouvacího políčka uprostřed posuvníku.</span><span class="sxs-lookup"><span data-stu-id="9436d-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="9436d-115">Kromě použití ke změně hodnoty panelu přejděte myší, můžete uživatele také přetáhnout posouvací políčko do jakéhokoli bodu na panelu.</span><span class="sxs-lookup"><span data-stu-id="9436d-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="9436d-116">Výsledná hodnota závisí na pozici posouvací políčko, ale je vždy v rozsahu <xref:System.Windows.Forms.ScrollBar.Minimum%2A> k <xref:System.Windows.Forms.ScrollBar.Maximum%2A> vlastnosti nastavený uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9436d-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="9436d-117">LargeChange a SmallChange vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9436d-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="9436d-118">Když uživatel stiskne klávesu PAGE UP nebo PAGE DOWN nebo klikne v sledovat panelu přejděte na obou stranách posouvací políčko, <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnotu nastavenou v <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9436d-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="9436d-119">Když uživatel stiskne jednu šipku klíče nebo klepne na jednu z tlačítka panelu přejděte <xref:System.Windows.Forms.ScrollBar.Value%2A> změny vlastností podle hodnotu nastavenou v <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9436d-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9436d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9436d-120">See Also</span></span>  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [<span data-ttu-id="9436d-121">Přidání do Windows Forms pro rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="9436d-121">Additions to Windows Forms for the .NET Framework 2.0</span></span>](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [<span data-ttu-id="9436d-122">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9436d-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
