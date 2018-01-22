---
title: "Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1232f1f091412017e22f29d529bf7c76b32a4b6d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="f99f7-102">Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu</span><span class="sxs-lookup"><span data-stu-id="f99f7-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="f99f7-103">Můžete provést kontrolu nad zarovnání na hranu svých formulářů podle nastavení <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="f99f7-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="f99f7-104">Tato vlastnost určuje, kde vlastní ovládací prvek nachází ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="f99f7-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="f99f7-105"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f99f7-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="f99f7-106">Nastavení</span><span class="sxs-lookup"><span data-stu-id="f99f7-106">Setting</span></span>|<span data-ttu-id="f99f7-107">Vliv na vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f99f7-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="f99f7-108">Překladišť k dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="f99f7-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="f99f7-109">Doplní veškerý zbývající prostor ve tvaru.</span><span class="sxs-lookup"><span data-stu-id="f99f7-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="f99f7-110">Přepraviště na levé straně formuláře.</span><span class="sxs-lookup"><span data-stu-id="f99f7-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="f99f7-111">Nepodporuje není ukotvení odkudkoli a zobrazí se v umístění určeném pomocí jeho <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="f99f7-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="f99f7-112">Přepraviště na pravé straně formuláře.</span><span class="sxs-lookup"><span data-stu-id="f99f7-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="f99f7-113">Překladišť k horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="f99f7-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="f99f7-114">Tyto hodnoty lze nastavit i v kódu.</span><span class="sxs-lookup"><span data-stu-id="f99f7-114">These values can also be set in code.</span></span> <span data-ttu-id="f99f7-115">Další informace najdete v tématu [postupy: zarovnání ovládacího prvku k okrajům formuláře](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f99f7-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f99f7-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f99f7-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f99f7-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f99f7-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f99f7-118">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f99f7-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="f99f7-119">Nastavit vlastnost ukotvení pro ovládací prvek v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f99f7-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="f99f7-120">V Návrháři formulářů Windows vyberte vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f99f7-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="f99f7-121">V **vlastnosti** klikněte na rozevírací seznam pole vedle <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f99f7-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="f99f7-122">Grafické rozhraní představující šesti možné <xref:System.Windows.Forms.Control.Dock%2A> nastavení se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="f99f7-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="f99f7-123">Vyberte příslušné nastavení.</span><span class="sxs-lookup"><span data-stu-id="f99f7-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="f99f7-124">Vlastní ovládací prvek bude nyní ukotvení způsobem zadané nastavení.</span><span class="sxs-lookup"><span data-stu-id="f99f7-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99f7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f99f7-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f99f7-126">Postupy: Zarovnávání ovládacího prvku k okrajům formulářů</span><span class="sxs-lookup"><span data-stu-id="f99f7-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="f99f7-127">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="f99f7-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="f99f7-128">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f99f7-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="f99f7-129">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f99f7-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="f99f7-130">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f99f7-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="f99f7-131">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f99f7-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="f99f7-132">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f99f7-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="f99f7-133">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f99f7-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
