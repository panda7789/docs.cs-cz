---
title: Ukotvení ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745520"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="ec664-102">Postupy: ukotvení ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec664-102">How to: Dock controls on Windows Forms</span></span>

<span data-ttu-id="ec664-103">Můžete ukotvit ovládací prvky do okrajů formuláře nebo je nechat vyplnit kontejner ovládacího prvku (buď formuláře nebo ovládacího prvku kontejneru).</span><span class="sxs-lookup"><span data-stu-id="ec664-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="ec664-104">Například Průzkumník Windows ukotví svůj <xref:System.Windows.Forms.TreeView> ovládací prvek na levou stranu okna a jeho <xref:System.Windows.Forms.ListView> ovládací prvek na pravou stranu okna.</span><span class="sxs-lookup"><span data-stu-id="ec664-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="ec664-105">Pomocí vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> pro všechny viditelné ovládací prvky model Windows Forms definujte režim ukotvení.</span><span class="sxs-lookup"><span data-stu-id="ec664-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>

> [!NOTE]
> <span data-ttu-id="ec664-106">Ovládací prvky jsou ukotveny v obráceném pořadí z.</span><span class="sxs-lookup"><span data-stu-id="ec664-106">Controls are docked in reverse z-order.</span></span>

<span data-ttu-id="ec664-107">Vlastnost <xref:System.Windows.Forms.Control.Dock%2A> komunikuje s vlastností <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec664-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="ec664-108">Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec664-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="to-dock-a-control"></a><span data-ttu-id="ec664-109">Ukotvení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ec664-109">To dock a control</span></span>

1. <span data-ttu-id="ec664-110">V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="ec664-110">In Visual Studio, select the control that you want to dock.</span></span>

2. <span data-ttu-id="ec664-111">V okně **vlastnosti** klikněte na šipku napravo od vlastnosti <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec664-111">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

   <span data-ttu-id="ec664-112">Zobrazí se editor, který zobrazuje řadu polí reprezentujících okraje a střed formuláře.</span><span class="sxs-lookup"><span data-stu-id="ec664-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>

3. <span data-ttu-id="ec664-113">Klikněte na tlačítko, které představuje okraj formuláře, kde chcete ovládací prvek ukotvit.</span><span class="sxs-lookup"><span data-stu-id="ec664-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="ec664-114">Chcete-li vyplnit obsah formuláře ovládacího prvku nebo ovládacího prvku kontejneru, klikněte na středový rámeček.</span><span class="sxs-lookup"><span data-stu-id="ec664-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="ec664-115">Chcete-li zakázat dokování, klikněte na tlačítko **(žádné)** .</span><span class="sxs-lookup"><span data-stu-id="ec664-115">Click **(none)** to disable docking.</span></span>

   <span data-ttu-id="ec664-116">Velikost ovládacího prvku je automaticky nastavena tak, aby odpovídala hranicím ukotveného okraje.</span><span class="sxs-lookup"><span data-stu-id="ec664-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ec664-117">Zděděné ovládací prvky musí být `Protected`, aby je bylo možné ukotvit.</span><span class="sxs-lookup"><span data-stu-id="ec664-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="ec664-118">Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho vlastnost **modifikátoru** v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="ec664-118">To change the access level of a control, set its **Modifier** property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec664-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec664-119">See also</span></span>

- [<span data-ttu-id="ec664-120">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="ec664-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="ec664-121">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="ec664-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="ec664-122">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec664-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="ec664-123">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="ec664-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="ec664-124">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ec664-124">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="ec664-125">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ec664-125">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="ec664-126">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="ec664-126">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="ec664-127">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec664-127">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
