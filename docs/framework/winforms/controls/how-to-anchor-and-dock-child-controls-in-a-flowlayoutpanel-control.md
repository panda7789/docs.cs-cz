---
title: "Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfcb802df01ce9d8f1cbaaf72dcf00d06028fb36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="a2254-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a2254-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="a2254-103"><xref:System.Windows.Forms.FlowLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastností v jejích podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a2254-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="a2254-104">Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a2254-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="a2254-105">Vytvoření <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="a2254-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="a2254-106">Nastavte <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> řídit k **300**a nastavit jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> k <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="a2254-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="a2254-107">Vytvořte dvě <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a2254-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="a2254-108">Nastavte <xref:System.Windows.Forms.Control.Width%2A> z na první tlačítko **200**.</span><span class="sxs-lookup"><span data-stu-id="a2254-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="a2254-109">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na druhý tlačítko <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="a2254-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a2254-110">Na druhé tlačítko předpokládá šířku stejné jako na první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a2254-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="a2254-111">Není funkce stretch přes celou šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a2254-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="a2254-112">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na druhý tlačítko `None`.</span><span class="sxs-lookup"><span data-stu-id="a2254-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="a2254-113">To způsobí, že tlačítko předpokládat, že původní šířku.</span><span class="sxs-lookup"><span data-stu-id="a2254-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="a2254-114">Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost na druhý tlačítko `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="a2254-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a2254-115">Na druhé tlačítko předpokládá šířku stejné jako na první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a2254-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="a2254-116">Není funkce stretch přes celou šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a2254-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="a2254-117">Toto je obecná pravidla pro ukotvení a dokování v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku: pro svislé toku pokynů <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku sloupec odvozených z ovládacího prvku nejširší podřízené ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="a2254-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="a2254-118">Všechny ostatní ovládací prvky v tomto sloupci se <xref:System.Windows.Forms.Control.Anchor%2A> nebo <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti jsou zarovnána nebo roztažen tak, aby vyhovovaly předpokládané sloupce.</span><span class="sxs-lookup"><span data-stu-id="a2254-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="a2254-119">Chování funguje podobným způsobem jako pro vodorovné toku pokynů.</span><span class="sxs-lookup"><span data-stu-id="a2254-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="a2254-120"><xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výšku řádku odvozených z nejvyšší podřízený ovládací prvek řádek, a všechny ukotveného nebo ukotvené podřízených ovládacích prvků v tomto řádku jsou zarovnána nebo přizpůsobí předpokládané řádek.</span><span class="sxs-lookup"><span data-stu-id="a2254-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2254-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2254-121">Example</span></span>  
 <span data-ttu-id="a2254-122">Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotven a ukotven relativně k blue tlačítka na <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="a2254-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="a2254-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="a2254-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="a2254-124">![FlowLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="a2254-124">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="a2254-125">Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotven a ukotven relativně k blue tlačítka na <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="a2254-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="a2254-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="a2254-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="a2254-127">![FlowLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="a2254-127">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="a2254-128">Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a2254-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2254-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a2254-129">Compiling the Code</span></span>  
 <span data-ttu-id="a2254-130">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a2254-130">This example requires:</span></span>  
  
-   <span data-ttu-id="a2254-131">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2254-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a2254-132">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a2254-132">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a2254-133">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="a2254-133">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="a2254-134">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a2254-134">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2254-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2254-135">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="a2254-136">Přehled ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a2254-136">FlowLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
