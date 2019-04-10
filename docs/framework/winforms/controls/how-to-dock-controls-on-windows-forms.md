---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317256"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="737f5-102">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="737f5-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="737f5-103">Můžete ukotvit ovládací prvky k okrajům formuláře nebo ho zadejte kontejneru ovládacího prvku (formuláře nebo ovládací prvek kontejneru).</span><span class="sxs-lookup"><span data-stu-id="737f5-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="737f5-104">Například Windows Explorer ukotvené jeho <xref:System.Windows.Forms.TreeView> ovládacího prvku na levé straně okna a jeho <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně okna.</span><span class="sxs-lookup"><span data-stu-id="737f5-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="737f5-105">Použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti pro všechny viditelné prvky Windows Forms k definování dokovací režimu.</span><span class="sxs-lookup"><span data-stu-id="737f5-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="737f5-106">Ovládací prvky jsou ukotveny v obráceném pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="737f5-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="737f5-107"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="737f5-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="737f5-108">Další informace najdete v tématu [přehled vlastnosti AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="737f5-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="737f5-109">Chcete-li ukotvit ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="737f5-109">To dock a control</span></span>  
  
1. <span data-ttu-id="737f5-110">Vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="737f5-110">Select the control that you want to dock.</span></span>  
  
2. <span data-ttu-id="737f5-111">V okně Vlastnosti klikněte na šipku vpravo od <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="737f5-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="737f5-112">Editoru se zobrazí, který zobrazuje řadu polí představující hrany a střed formuláře.</span><span class="sxs-lookup"><span data-stu-id="737f5-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3. <span data-ttu-id="737f5-113">Klikněte na tlačítko, který představuje edge formuláře, ve které chcete ukotvit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="737f5-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="737f5-114">K vyplnění obsah ovládacího prvku formulář nebo ovládací prvek kontejneru, klikněte na tlačítko prostředním poli.</span><span class="sxs-lookup"><span data-stu-id="737f5-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="737f5-115">Klikněte na tlačítko **(žádný)** zakázat ukotvení.</span><span class="sxs-lookup"><span data-stu-id="737f5-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="737f5-116">Ovládací prvek automaticky se přizpůsobí hranice ukotvených edge.</span><span class="sxs-lookup"><span data-stu-id="737f5-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="737f5-117">Zděděný ovládací prvky musí být `Protected` lze ukotvit.</span><span class="sxs-lookup"><span data-stu-id="737f5-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="737f5-118">Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho **modifikátor** vlastností v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="737f5-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737f5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="737f5-119">See also</span></span>

- [<span data-ttu-id="737f5-120">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="737f5-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="737f5-121">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="737f5-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="737f5-122">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="737f5-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="737f5-123">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="737f5-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="737f5-124">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="737f5-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="737f5-125">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="737f5-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="737f5-126">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="737f5-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="737f5-127">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="737f5-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="737f5-128">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="737f5-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
