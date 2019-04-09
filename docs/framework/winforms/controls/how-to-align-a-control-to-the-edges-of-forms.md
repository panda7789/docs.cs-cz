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
ms.openlocfilehash: 990fc996cfb5ecf4d9fde255ad026e3f46a24718
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185780"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="9d4c3-102">Postupy: Zarovnávání ovládacího prvku k okrajům formulářů</span><span class="sxs-lookup"><span data-stu-id="9d4c3-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="9d4c3-103">Můžete provést ovládacího prvku zarovná na hraničních zařízeních formulářů tím, že nastavíte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="9d4c3-104">Tato vlastnost určuje, kde se nachází váš ovládací prvek ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="9d4c3-105"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="9d4c3-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="9d4c3-106">Nastavení</span><span class="sxs-lookup"><span data-stu-id="9d4c3-106">Setting</span></span>|<span data-ttu-id="9d4c3-107">Vliv na váš ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9d4c3-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="9d4c3-108">Ukotví do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="9d4c3-109">Vyplní veškerý zbývající prostor ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="9d4c3-110">Ukotví na levou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="9d4c3-111">Fakturuje se u není dock kdekoli a zobrazí se v umístění určeném jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="9d4c3-112">Ukotví na pravou stranu formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="9d4c3-113">Ukotví do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="9d4c3-114">Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="9d4c3-115">Chcete-li nastavit vlastnosti Dock ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="9d4c3-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="9d4c3-116">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> k odpovídající hodnotě v kódu.</span><span class="sxs-lookup"><span data-stu-id="9d4c3-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d4c3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d4c3-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9d4c3-118">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d4c3-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9d4c3-119">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9d4c3-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="9d4c3-120">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9d4c3-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="9d4c3-121">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="9d4c3-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
