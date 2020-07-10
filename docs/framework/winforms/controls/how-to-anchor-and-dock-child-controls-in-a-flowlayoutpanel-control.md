---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
description: Přečtěte si, jak programově ukotvit a ukotvit podřízené ovládací prvky v model Windows Forms ovládacím prvku FlowLayoutPanel.
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174533"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="fbd08-103">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fbd08-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="fbd08-104"><xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek podporuje <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti a <xref:System.Windows.Forms.Control.Dock%2A> v jeho podřízených ovládacích prvcích.</span><span class="sxs-lookup"><span data-stu-id="fbd08-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="fbd08-105">Ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fbd08-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="fbd08-106">Vytvořte <xref:System.Windows.Forms.FlowLayoutPanel> na formuláři ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fbd08-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="fbd08-107">Nastavte <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na **300**a nastavte jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="fbd08-108">Vytvořte dva <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="fbd08-109">Nastavte <xref:System.Windows.Forms.Control.Width%2A> první tlačítko na **200**.</span><span class="sxs-lookup"><span data-stu-id="fbd08-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="fbd08-110">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhého tlačítka na <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fbd08-111">Druhé tlačítko předpokládá stejnou šířku jako první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fbd08-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="fbd08-112">Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="fbd08-113">Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhého tlačítka na `None` .</span><span class="sxs-lookup"><span data-stu-id="fbd08-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="fbd08-114">Tím dojde k tomu, že tlačítko bude předpokládat původní šířku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="fbd08-115">Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost druhého tlačítka na `Left, Right` .</span><span class="sxs-lookup"><span data-stu-id="fbd08-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fbd08-116">Druhé tlačítko předpokládá stejnou šířku jako první tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fbd08-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="fbd08-117">Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="fbd08-118">Toto je obecné pravidlo pro ukotvení a ukotvení v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku: pro Směr svislého toku <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku implicitního sloupce z nejširšího podřízeného ovládacího prvku ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="fbd08-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="fbd08-119">Všechny ostatní ovládací prvky v tomto sloupci <xref:System.Windows.Forms.Control.Anchor%2A> s <xref:System.Windows.Forms.Control.Dock%2A> vlastnostmi nebo se zarovnají nebo roztáhnou tak, aby se vešly do tohoto implicitního sloupce.</span><span class="sxs-lookup"><span data-stu-id="fbd08-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="fbd08-120">Chování funguje podobným způsobem jako u horizontálních směrů toku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="fbd08-121"><xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek vypočítá výšku implicitního řádku z největšího podřízeného ovládacího prvku na řádku a všechny ukotvené nebo ukotvené podřízené ovládací prvky na tomto řádku jsou zarovnány nebo upraveny tak, aby odpovídaly předpokládanému řádku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="fbd08-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbd08-122">Example</span></span>

<span data-ttu-id="fbd08-123">Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="fbd08-124"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Je <xref:System.Windows.Forms.FlowDirection.LeftToRight> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="fbd08-125">![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="fbd08-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="fbd08-126">Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="fbd08-127"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Je <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="fbd08-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="fbd08-128">![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="fbd08-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="fbd08-129">Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> ovládacího prvku v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="fbd08-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="fbd08-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fbd08-130">Compiling the Code</span></span>

<span data-ttu-id="fbd08-131">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="fbd08-131">This example requires:</span></span>

- <span data-ttu-id="fbd08-132">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="fbd08-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd08-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbd08-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="fbd08-134">FlowLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fbd08-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
