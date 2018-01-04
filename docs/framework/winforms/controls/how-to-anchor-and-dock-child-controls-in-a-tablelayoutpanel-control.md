---
title: "Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56909c823beca99d277bfbf7a20d39663bcd44ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="ad851-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ad851-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="ad851-103"><xref:System.Windows.Forms.TableLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastností v jejích podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ad851-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="ad851-104">Chcete-li zarovnat podřízený ovládací prvek v buňce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ad851-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="ad851-105">Vytvoření <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ad851-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="ad851-106">Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> a <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> vlastnosti, které chcete **1**.</span><span class="sxs-lookup"><span data-stu-id="ad851-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="ad851-107">Vytvoření <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ad851-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="ad851-108"><xref:System.Windows.Forms.Button> Sídlí levém horním rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="ad851-109">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left`.</span><span class="sxs-lookup"><span data-stu-id="ad851-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="ad851-110"><xref:System.Windows.Forms.Button> Řízení přesune vyrovnání levého okraje buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad851-111">Toto chování se liší od chování další ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ad851-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="ad851-112">V další ovládací prvky kontejneru ovládacího prvku podřízené nepřesouvá při <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost nastavena a vzdálenost mezi ukotvené ovládacího prvku a hranic nadřazený kontejner vyřešen v době <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena.</span><span class="sxs-lookup"><span data-stu-id="ad851-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="ad851-113">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="ad851-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="ad851-114"><xref:System.Windows.Forms.Button> Řízení přesune tak, aby zabíral levém horním rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="ad851-115">Opakujte krok 5 s hodnotou z `Top, Right` přesunout <xref:System.Windows.Forms.Button> řízení pravém horním rohu buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="ad851-116">Opakování s hodnotami `Bottom, Left` a `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="ad851-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="ad851-117">K roztahování podřízený ovládací prvek v buňce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ad851-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="ad851-118">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="ad851-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="ad851-119"><xref:System.Windows.Forms.Button> Po změně velikosti k roztahování napříč buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad851-120">Toto chování se liší od chování další ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ad851-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="ad851-121">V další ovládací prvky kontejneru podřízený ovládací prvek není při změně velikosti <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena na `Left, Right` nebo `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="ad851-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="ad851-122">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="ad851-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="ad851-123"><xref:System.Windows.Forms.Button> Po změně velikosti k roztahování z horní části do dolní části buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="ad851-124">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="ad851-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="ad851-125"><xref:System.Windows.Forms.Button> Po změně velikosti k vyplnění buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="ad851-126">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `None`.</span><span class="sxs-lookup"><span data-stu-id="ad851-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="ad851-127"><xref:System.Windows.Forms.Button> Změně velikosti nebo zarovnaný na střed v buňce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ad851-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="ad851-128">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="ad851-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="ad851-129"><xref:System.Windows.Forms.Button> Řízení přesune vyrovnání levého okraje buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="ad851-130"><xref:System.Windows.Forms.Button> Ovládací prvek zachovává jeho šířka, ale jeho výšku se změnila velikost k vyplnění buňky svisle.</span><span class="sxs-lookup"><span data-stu-id="ad851-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad851-131">Toto je stejné chování, k níž dojde v další ovládací prvky kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ad851-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="ad851-132">Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ad851-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="ad851-133"><xref:System.Windows.Forms.Button> Po změně velikosti k vyplnění buňky.</span><span class="sxs-lookup"><span data-stu-id="ad851-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad851-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad851-134">Example</span></span>  
 <span data-ttu-id="ad851-135">Následující obrázek znázorňuje pět tlačítek ukotvené v pěti samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.</span><span class="sxs-lookup"><span data-stu-id="ad851-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ad851-136">![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="ad851-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="ad851-137">Následující obrázek znázorňuje čtyři tlačítka ukotvené v rozích čtyři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.</span><span class="sxs-lookup"><span data-stu-id="ad851-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ad851-138">![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="ad851-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="ad851-139">Následující obrázek znázorňuje tři tlačítka roztažen tak podle ukotvení v tři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.</span><span class="sxs-lookup"><span data-stu-id="ad851-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="ad851-140">![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="ad851-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="ad851-141">Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ad851-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad851-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ad851-142">Compiling the Code</span></span>  
 <span data-ttu-id="ad851-143">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ad851-143">This example requires:</span></span>  
  
-   <span data-ttu-id="ad851-144">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="ad851-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ad851-145">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ad851-145">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ad851-146">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="ad851-146">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="ad851-147">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ad851-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad851-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad851-148">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="ad851-149">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ad851-149">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
