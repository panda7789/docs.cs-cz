---
title: 'Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210371"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="60d0a-102">Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu</span><span class="sxs-lookup"><span data-stu-id="60d0a-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>

<span data-ttu-id="60d0a-103">Zarovnat na hranici formulářů tím, že nastavíte hodnotu ovládacího prvku můžete provést <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="60d0a-103">You can make your control align to the edge of your forms by setting the value of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="60d0a-104">Tato vlastnost určuje, kde se nachází váš ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="60d0a-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="60d0a-105"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="60d0a-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="60d0a-106">Nastavení</span><span class="sxs-lookup"><span data-stu-id="60d0a-106">Setting</span></span>|<span data-ttu-id="60d0a-107">Vliv na váš ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="60d0a-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="60d0a-108">Ukotví do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="60d0a-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="60d0a-109">Vyplní veškerý zbývající prostor ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="60d0a-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="60d0a-110">Ukotví na levou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="60d0a-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="60d0a-111">Fakturuje se u není dock kdekoli a zobrazí se v umístění určeném jeho <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="60d0a-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="60d0a-112">Ukotví na pravou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="60d0a-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="60d0a-113">Ukotví do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="60d0a-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="60d0a-114">Tyto hodnoty můžete také nastavit v kódu.</span><span class="sxs-lookup"><span data-stu-id="60d0a-114">These values can also be set in code.</span></span> <span data-ttu-id="60d0a-115">Další informace najdete v tématu [jak: Zarovnání ovládacího prvku k okrajům formulářů](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="60d0a-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>

## <a name="set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="60d0a-116">Nastavení vlastnosti Dock ovládacího prvku v době návrhu</span><span class="sxs-lookup"><span data-stu-id="60d0a-116">Set the Dock property for your control at design time</span></span>

1. <span data-ttu-id="60d0a-117">V Návrháři formulářů Windows v sadě Visual Studio vyberte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="60d0a-117">In the Windows Forms Designer in Visual Studio, select your control.</span></span>

2. <span data-ttu-id="60d0a-118">V **vlastnosti** okna, klikněte na tlačítko Další pole rozevíracího seznamu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="60d0a-118">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

     <span data-ttu-id="60d0a-119">Grafické rozhraní představující šest možných <xref:System.Windows.Forms.Control.Dock%2A> nastavení se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="60d0a-119">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>

3. <span data-ttu-id="60d0a-120">Vyberte příslušné nastavení.</span><span class="sxs-lookup"><span data-stu-id="60d0a-120">Choose the appropriate setting.</span></span>

4. <span data-ttu-id="60d0a-121">Ovládací prvek bude nyní ukotvit způsobem popsaným v nastavení.</span><span class="sxs-lookup"><span data-stu-id="60d0a-121">Your control will now dock in the manner specified by the setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="60d0a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60d0a-122">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="60d0a-123">Postupy: Zarovnání ovládacího prvku k okrajům formulářů</span><span class="sxs-lookup"><span data-stu-id="60d0a-123">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="60d0a-124">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="60d0a-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="60d0a-125">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60d0a-125">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="60d0a-126">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="60d0a-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="60d0a-127">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="60d0a-127">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="60d0a-128">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="60d0a-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="60d0a-129">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="60d0a-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="60d0a-130">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="60d0a-130">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
