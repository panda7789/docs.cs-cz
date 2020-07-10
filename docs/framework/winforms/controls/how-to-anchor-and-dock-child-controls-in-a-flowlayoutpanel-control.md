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
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel

<xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek podporuje <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti a <xref:System.Windows.Forms.Control.Dock%2A> v jeho podřízených ovládacích prvcích.

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel

1. Vytvořte <xref:System.Windows.Forms.FlowLayoutPanel> na formuláři ovládací prvek.

2. Nastavte <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na **300**a nastavte jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .

3. Vytvořte dva <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

4. Nastavte <xref:System.Windows.Forms.Control.Width%2A> první tlačítko na **200**.

5. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhého tlačítka na <xref:System.Windows.Forms.DockStyle.Fill> .

    > [!NOTE]
    > Druhé tlačítko předpokládá stejnou šířku jako první tlačítko. Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

6. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhého tlačítka na `None` . Tím dojde k tomu, že tlačítko bude předpokládat původní šířku.

7. Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost druhého tlačítka na `Left, Right` .

    > [!IMPORTANT]
    > Druhé tlačítko předpokládá stejnou šířku jako první tlačítko. Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Toto je obecné pravidlo pro ukotvení a ukotvení v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku: pro Směr svislého toku <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku implicitního sloupce z nejširšího podřízeného ovládacího prvku ve sloupci. Všechny ostatní ovládací prvky v tomto sloupci <xref:System.Windows.Forms.Control.Anchor%2A> s <xref:System.Windows.Forms.Control.Dock%2A> vlastnostmi nebo se zarovnají nebo roztáhnou tak, aby se vešly do tohoto implicitního sloupce. Chování funguje podobným způsobem jako u horizontálních směrů toku. <xref:System.Windows.Forms.FlowLayoutPanel>Ovládací prvek vypočítá výšku implicitního řádku z největšího podřízeného ovládacího prvku na řádku a všechny ukotvené nebo ukotvené podřízené ovládací prvky na tomto řádku jsou zarovnány nebo upraveny tak, aby odpovídaly předpokládanému řádku.

## <a name="example"></a>Příklad

Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Je <xref:System.Windows.Forms.FlowDirection.LeftToRight> .

![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Je <xref:System.Windows.Forms.FlowDirection.TopDown> .

![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")

Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> ovládacího prvku v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku.

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel – přehled ovládacího prvku](flowlayoutpanel-control-overview.md)
