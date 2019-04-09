---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 679333186d9f9b791e5ad9c2e1cb74f69e051a62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168542"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="ec6b5-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ec6b5-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="ec6b5-103"><xref:System.Windows.Forms.FlowLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti v jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="ec6b5-104">A ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ec6b5-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="ec6b5-105">Vytvoření <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="ec6b5-106">Nastavte <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> mít pod kontrolou **300**a nastavte jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> k <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="ec6b5-107">Pak vytvoříte další dva <xref:System.Windows.Forms.Button> ovládací prvky a umístit je <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="ec6b5-108">Nastavte <xref:System.Windows.Forms.Control.Width%2A> první tlačítka **200**.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="ec6b5-109">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhé tlačítko do <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec6b5-110">Na druhé tlačítko předpokládá stejnou šířku prvního tlačítka.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="ec6b5-111">Není roztáhnout na šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="ec6b5-112">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhé tlačítko do `None`.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="ec6b5-113">To způsobí, že tlačítko předpokládat, že jeho původní šířka.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="ec6b5-114">Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost druhé tlačítko do `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ec6b5-115">Na druhé tlačítko předpokládá stejnou šířku prvního tlačítka.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="ec6b5-116">Není roztáhnout na šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="ec6b5-117">Toto je obecné pravidlo pro ukotvení a dokování v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku: směrech svislé tok <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku implicitní sloupce z nejširší podřízený ovládací prvek ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="ec6b5-118">Všechny ostatní ovládací prvky v tomto sloupci se <xref:System.Windows.Forms.Control.Anchor%2A> nebo <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti jsou zarovnána, nebo roztažená do přizpůsobit tento sloupec implicitní.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="ec6b5-119">Chování funguje podobným způsobem jako směry vodorovné toku.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="ec6b5-120"><xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výška implicitní řádek z nejvyšší podřízený ovládací prvek v řádku, a všechny ukotvené nebo ukotvené podřízené ovládací prvky v tomto řádku jsou zarovnána nebo velikostí podle předpokládané řádek.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec6b5-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec6b5-121">Example</span></span>  
 <span data-ttu-id="ec6b5-122">Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotvena a ukotven vzhledem k modrého tlačítka v <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="ec6b5-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="ec6b5-124">![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="ec6b5-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="ec6b5-125">Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotvena a ukotven vzhledem k modrého tlačítka v <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="ec6b5-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="ec6b5-127">![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="ec6b5-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="ec6b5-128">Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnot vlastností pro <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec6b5-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ec6b5-129">Compiling the Code</span></span>  
 <span data-ttu-id="ec6b5-130">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ec6b5-130">This example requires:</span></span>  
  
-   <span data-ttu-id="ec6b5-131">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ec6b5-132">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ec6b5-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ec6b5-133">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="ec6b5-133">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6b5-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec6b5-134">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="ec6b5-135">FlowLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ec6b5-135">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
