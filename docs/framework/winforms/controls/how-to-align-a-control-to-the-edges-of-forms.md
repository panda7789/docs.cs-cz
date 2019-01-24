---
title: 'Postupy: Zarovnání ovládacího prvku k okrajům formulářů'
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
ms.openlocfilehash: ba5e9fc92f2805206f6c3796689898f3ff845896
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610406"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="32e44-102">Postupy: Zarovnání ovládacího prvku k okrajům formulářů</span><span class="sxs-lookup"><span data-stu-id="32e44-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="32e44-103">Můžete provést ovládacího prvku zarovná na hraničních zařízeních formulářů tím, že nastavíte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="32e44-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="32e44-104">Tato vlastnost určuje, kde se nachází váš ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="32e44-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="32e44-105"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="32e44-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="32e44-106">Nastavení</span><span class="sxs-lookup"><span data-stu-id="32e44-106">Setting</span></span>|<span data-ttu-id="32e44-107">Vliv na váš ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="32e44-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="32e44-108">Ukotví do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="32e44-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="32e44-109">Vyplní veškerý zbývající prostor ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="32e44-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="32e44-110">Ukotví na levou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="32e44-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="32e44-111">Fakturuje se u není dock kdekoli a zobrazí se v umístění určeném jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="32e44-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="32e44-112">Ukotví na pravou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="32e44-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="32e44-113">Ukotví do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="32e44-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="32e44-114">Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32e44-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="32e44-115">Chcete-li nastavit vlastnosti Dock ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="32e44-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="32e44-116">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> k odpovídající hodnotě v kódu.</span><span class="sxs-lookup"><span data-stu-id="32e44-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32e44-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32e44-117">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="32e44-118">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32e44-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="32e44-119">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="32e44-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="32e44-120">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="32e44-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="32e44-121">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="32e44-121">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
