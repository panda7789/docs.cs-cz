---
title: 'Postupy: Zarovnávání ovládacího prvku k okrajům formulářů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015947"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="4f991-102">Postupy: Zarovnávání ovládacího prvku k okrajům formulářů</span><span class="sxs-lookup"><span data-stu-id="4f991-102">How to: Align a Control to the Edges of Forms</span></span>

<span data-ttu-id="4f991-103">Můžete nastavit, aby se ovládací prvek na okraji formulářů narovnal nastavením <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4f991-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="4f991-104">Tato vlastnost určuje, kde se ovládací prvek nachází ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="4f991-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="4f991-105"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost může být nastavena na následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4f991-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="4f991-106">Nastavení</span><span class="sxs-lookup"><span data-stu-id="4f991-106">Setting</span></span>|<span data-ttu-id="4f991-107">Vliv na ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4f991-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="4f991-108">Docker do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f991-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="4f991-109">Vyplní všechny zbývající místo ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="4f991-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="4f991-110">Dockers na levou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f991-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="4f991-111">Není ukotven kdekoli a zobrazí se v umístění určeném <xref:System.Windows.Forms.Control.Location%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="4f991-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="4f991-112">Dockers na pravou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f991-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="4f991-113">Docker do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f991-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="4f991-114">Pro tuto funkci v aplikaci Visual Studio je podporována podpora v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="4f991-114">There is design-time support for this feature in Visual Studio.</span></span>

## <a name="set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="4f991-115">Nastavit vlastnost Dock pro váš ovládací prvek v době běhu</span><span class="sxs-lookup"><span data-stu-id="4f991-115">Set the Dock property for your control at run time</span></span>

<span data-ttu-id="4f991-116"><xref:System.Windows.Forms.Control.Dock%2A> Nastavte vlastnost na odpovídající hodnotu v kódu.</span><span class="sxs-lookup"><span data-stu-id="4f991-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a><span data-ttu-id="4f991-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f991-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f991-118">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f991-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="4f991-119">Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4f991-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="4f991-120">Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4f991-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="4f991-121">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="4f991-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
