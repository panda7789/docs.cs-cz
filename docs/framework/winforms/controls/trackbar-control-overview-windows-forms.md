---
title: "TrackBar – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccea982c45ab22a4b2ab81bc80c16dd472144bbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="0fe8c-102">TrackBar – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0fe8c-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="0fe8c-103">Windows Forms <xref:System.Windows.Forms.TrackBar> ovládací prvek (také někdy nazývané "posuvník") se používá pro procházení velké množství informací nebo vizuálně úpravě číselné nastavení.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="0fe8c-104"><xref:System.Windows.Forms.TrackBar> Řízení má dvě části: jezdce, také známé jako jezdce a značek.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="0fe8c-105">Jezdce je část, která se dá upravit.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="0fe8c-106">Odpovídá jeho umístění <xref:System.Windows.Forms.TrackBar.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="0fe8c-107">Značky jsou visual indikátory, které jsou rozmístěny v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="0fe8c-108">Pozice přesouvají v krocích, které můžete zadat a lze zarovnávat vodorovně nebo svisle.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="0fe8c-109">Panelu sledování můžete například použít k řízení rychlost blikání kurzoru míry nebo myš pro systém.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="0fe8c-110">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0fe8c-110">Key Properties</span></span>  
 <span data-ttu-id="0fe8c-111">Klíčové vlastnosti <xref:System.Windows.Forms.TrackBar> řízení, představují <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, a <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="0fe8c-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>je mezery o rysky.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="0fe8c-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>a <xref:System.Windows.Forms.TrackBar.Maximum%2A> jsou nejnižší a nejvyšší hodnoty, které může být reprezentován na panelu sledovat.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="0fe8c-114">Jsou dvě důležité vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> a <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="0fe8c-115">Hodnota <xref:System.Windows.Forms.TrackBar.SmallChange%2A> vlastnost je počet pozic úchytu přesune v reakci na LEVÉ a pravé šipky klíče stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="0fe8c-116">Hodnota <xref:System.Windows.Forms.TrackBar.LargeChange%2A> vlastnost je počet pozic úchytu přesune v reakci na situaci, kdy stisknuta klávesa PAGE UP nebo PAGE DOWN nebo v reakci na myši klikne na panelu sledovat na obou stranách od jezdce.</span><span class="sxs-lookup"><span data-stu-id="0fe8c-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe8c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fe8c-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="0fe8c-118">TrackBar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="0fe8c-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
