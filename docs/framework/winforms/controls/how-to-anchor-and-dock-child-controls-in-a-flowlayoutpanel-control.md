---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 9a00fcd53211dd126c0e9203d6d577959b971e70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922910"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="e2be7-102">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e2be7-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="e2be7-103">Ovládací prvek podporuje vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> a v jeho podřízených ovládacích prvcích. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="e2be7-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="e2be7-104">Ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e2be7-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="e2be7-105">Vytvořte na formuláři ovládací prvek. <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="e2be7-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="e2be7-106"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>Nastavte ovládací prvek na 300 a nastavte jeho na. <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Width%2A></span><span class="sxs-lookup"><span data-stu-id="e2be7-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="e2be7-107">Vytvořte dva <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je <xref:System.Windows.Forms.FlowLayoutPanel> do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="e2be7-108">Nastavte první tlačítko na **200.** <xref:System.Windows.Forms.Control.Width%2A></span><span class="sxs-lookup"><span data-stu-id="e2be7-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="e2be7-109">Nastavte vlastnost druhého tlačítka na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="e2be7-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e2be7-110">Druhé tlačítko předpokládá stejnou šířku jako první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e2be7-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="e2be7-111">Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="e2be7-112">Nastavte vlastnost druhého tlačítka na `None`. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="e2be7-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="e2be7-113">Tím dojde k tomu, že tlačítko bude předpokládat původní šířku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="e2be7-114">Nastavte vlastnost druhého tlačítka na `Left, Right`. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="e2be7-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e2be7-115">Druhé tlačítko předpokládá stejnou šířku jako první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e2be7-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="e2be7-116">Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="e2be7-117">Toto je obecné pravidlo pro ukotvení a ukotvení v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku: pro směr <xref:System.Windows.Forms.FlowLayoutPanel> svislého toku ovládací prvek vypočítá šířku implicitního sloupce z nejširšího podřízeného ovládacího prvku ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="e2be7-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="e2be7-118">Všechny ostatní ovládací prvky v tomto sloupci <xref:System.Windows.Forms.Control.Anchor%2A> s <xref:System.Windows.Forms.Control.Dock%2A> vlastnostmi nebo se zarovnají nebo roztáhnou tak, aby se vešly do tohoto implicitního sloupce.</span><span class="sxs-lookup"><span data-stu-id="e2be7-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="e2be7-119">Chování funguje podobným způsobem jako u horizontálních směrů toku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="e2be7-120"><xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výšku implicitního řádku z největšího podřízeného ovládacího prvku na řádku a všechny ukotvené nebo ukotvené podřízené ovládací prvky na tomto řádku jsou zarovnány nebo upraveny tak, aby odpovídaly předpokládanému řádku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2be7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2be7-121">Example</span></span>  
 <span data-ttu-id="e2be7-122">Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="e2be7-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="e2be7-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je .<xref:System.Windows.Forms.FlowDirection.LeftToRight></span><span class="sxs-lookup"><span data-stu-id="e2be7-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="e2be7-124">![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="e2be7-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="e2be7-125">Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="e2be7-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="e2be7-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je .<xref:System.Windows.Forms.FlowDirection.TopDown></span><span class="sxs-lookup"><span data-stu-id="e2be7-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="e2be7-127">![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="e2be7-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="e2be7-128">Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty <xref:System.Windows.Forms.Button> vlastností ovládacího prvku v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e2be7-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2be7-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e2be7-129">Compiling the Code</span></span>  
 <span data-ttu-id="e2be7-130">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e2be7-130">This example requires:</span></span>  
  
- <span data-ttu-id="e2be7-131">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="e2be7-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2be7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2be7-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="e2be7-133">Přehled ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e2be7-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
