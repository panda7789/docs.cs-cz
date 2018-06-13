---
title: 'Postupy: Ukotvování ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532313"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="c1806-102">Postupy: Ukotvování ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1806-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="c1806-103">Můžete ukotvení ovládací prvky hrany svého formuláře nebo kliknul vyplnění kontejneru ovládacího prvku (formuláře nebo ovládacího prvku kontejneru).</span><span class="sxs-lookup"><span data-stu-id="c1806-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="c1806-104">Například Průzkumník Windows ukotvené jeho <xref:System.Windows.Forms.TreeView> ovládacího prvku na levé straně okna a jeho <xref:System.Windows.Forms.ListView> ovládacího prvku na pravé straně okna.</span><span class="sxs-lookup"><span data-stu-id="c1806-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="c1806-105">Použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost pro všechny viditelné ovládací prvky Windows Forms k definování ukotvení režimu.</span><span class="sxs-lookup"><span data-stu-id="c1806-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1806-106">Ovládací prvky jsou ukotven v obráceném pořadí z.</span><span class="sxs-lookup"><span data-stu-id="c1806-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="c1806-107"><xref:System.Windows.Forms.Control.Dock%2A> Vlastnost komunikuje s <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c1806-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="c1806-108">Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1806-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="c1806-109">Chcete-li ukotvit ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c1806-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="c1806-110">Vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="c1806-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="c1806-111">V okně vlastností klikněte na šipku napravo <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c1806-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="c1806-112">Editor se zobrazí, které zobrazuje sérii polí představující hrany a střed tvaru.</span><span class="sxs-lookup"><span data-stu-id="c1806-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="c1806-113">Klikněte na tlačítko, který představuje hrany formuláře, které chcete ukotvit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1806-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="c1806-114">K vyplnění obsah ovládacího prvku formuláře nebo ovládacího prvku kontejneru, klikněte na políčko center.</span><span class="sxs-lookup"><span data-stu-id="c1806-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="c1806-115">Klikněte na tlačítko **(none)** zakázat ukotvení.</span><span class="sxs-lookup"><span data-stu-id="c1806-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="c1806-116">Ovládací prvek automaticky se přizpůsobí hranice ukotveného okraj.</span><span class="sxs-lookup"><span data-stu-id="c1806-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1806-117">Musí být zděděné ovládací prvky `Protected` moct ukotvit.</span><span class="sxs-lookup"><span data-stu-id="c1806-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="c1806-118">Chcete-li změnit úroveň přístupu tohoto ovládacího prvku, nastavte jeho **modifikátor** vlastnost v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c1806-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1806-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1806-119">See Also</span></span>  
 [<span data-ttu-id="c1806-120">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c1806-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="c1806-121">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1806-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="c1806-122">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="c1806-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="c1806-123">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1806-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="c1806-124">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="c1806-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="c1806-125">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1806-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="c1806-126">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1806-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="c1806-127">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="c1806-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="c1806-128">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c1806-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
