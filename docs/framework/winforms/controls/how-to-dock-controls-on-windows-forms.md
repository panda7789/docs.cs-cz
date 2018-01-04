---
title: "Postupy: Ukotvování ovládacích prvků ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7227ee46f127070b44771a56a89b82bd0930ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="d27a9-102">Postupy: Ukotvování ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d27a9-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="d27a9-103">Můžete ukotvení ovládací prvky hrany svého formuláře nebo kliknul vyplnění kontejneru ovládacího prvku (formuláře nebo ovládacího prvku kontejneru).</span><span class="sxs-lookup"><span data-stu-id="d27a9-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="d27a9-104">Například Průzkumník Windows ukotvené jeho <xref:System.Windows.Forms.TreeView> ovládacího prvku na levé straně okna a jeho <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně okna.</span><span class="sxs-lookup"><span data-stu-id="d27a9-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="d27a9-105">Použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost pro všechny viditelné ovládací prvky Windows Forms k definování ukotvení režimu.</span><span class="sxs-lookup"><span data-stu-id="d27a9-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d27a9-106">Ovládací prvky jsou ukotven v obráceném pořadí z.</span><span class="sxs-lookup"><span data-stu-id="d27a9-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="d27a9-107"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje s <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d27a9-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="d27a9-108">Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d27a9-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="d27a9-109">Chcete-li ukotvit ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d27a9-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="d27a9-110">Vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="d27a9-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="d27a9-111">V okně vlastností klikněte na šipku napravo <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d27a9-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="d27a9-112">Editor se zobrazí, které zobrazuje sérii polí představující hrany a střed tvaru.</span><span class="sxs-lookup"><span data-stu-id="d27a9-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="d27a9-113">Klikněte na tlačítko, který představuje hrany formuláře, které chcete ukotvit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d27a9-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="d27a9-114">K vyplnění obsah ovládacího prvku formuláře nebo ovládacího prvku kontejneru, klikněte na políčko center.</span><span class="sxs-lookup"><span data-stu-id="d27a9-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="d27a9-115">Klikněte na tlačítko **(none)** zakázat ukotvení.</span><span class="sxs-lookup"><span data-stu-id="d27a9-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="d27a9-116">Ovládací prvek automaticky se přizpůsobí hranice ukotveného okraj.</span><span class="sxs-lookup"><span data-stu-id="d27a9-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d27a9-117">Musí být zděděné ovládací prvky `Protected` moct ukotvit.</span><span class="sxs-lookup"><span data-stu-id="d27a9-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="d27a9-118">Chcete-li změnit úroveň přístupu tohoto ovládacího prvku, nastavte jeho **modifikátor** vlastnost v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d27a9-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27a9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d27a9-119">See Also</span></span>  
 [<span data-ttu-id="d27a9-120">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d27a9-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="d27a9-121">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d27a9-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="d27a9-122">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="d27a9-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="d27a9-123">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d27a9-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="d27a9-124">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="d27a9-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="d27a9-125">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d27a9-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="d27a9-126">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d27a9-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="d27a9-127">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="d27a9-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="d27a9-128">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d27a9-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
