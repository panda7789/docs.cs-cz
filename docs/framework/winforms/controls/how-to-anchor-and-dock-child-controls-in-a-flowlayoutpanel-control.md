---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 3e9a5be944e199254ddb9cee0772c4d55be8fb77
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046071"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel

Ovládací prvek podporuje vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> a v jeho podřízených ovládacích prvcích. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel

1. Vytvořte na formuláři ovládací prvek. <xref:System.Windows.Forms.FlowLayoutPanel>

2. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>Nastavte ovládací prvek na 300 a nastavte jeho na. <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Width%2A>

3. Vytvořte dva <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je <xref:System.Windows.Forms.FlowLayoutPanel> do ovládacího prvku.

4. Nastavte první tlačítko na **200.** <xref:System.Windows.Forms.Control.Width%2A>

5. Nastavte vlastnost druhého tlačítka na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.Dock%2A>

    > [!NOTE]
    > Druhé tlačítko předpokládá stejnou šířku jako první tlačítko. Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

6. Nastavte vlastnost druhého tlačítka na `None`. <xref:System.Windows.Forms.Control.Dock%2A> Tím dojde k tomu, že tlačítko bude předpokládat původní šířku.

7. Nastavte vlastnost druhého tlačítka na `Left, Right`. <xref:System.Windows.Forms.Control.Anchor%2A>

    > [!IMPORTANT]
    > Druhé tlačítko předpokládá stejnou šířku jako první tlačítko. Neprovádí roztažení mezi celou šířkou <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Toto je obecné pravidlo pro ukotvení a ukotvení v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku: pro směr <xref:System.Windows.Forms.FlowLayoutPanel> svislého toku ovládací prvek vypočítá šířku implicitního sloupce z nejširšího podřízeného ovládacího prvku ve sloupci. Všechny ostatní ovládací prvky v tomto sloupci <xref:System.Windows.Forms.Control.Anchor%2A> s <xref:System.Windows.Forms.Control.Dock%2A> vlastnostmi nebo se zarovnají nebo roztáhnou tak, aby se vešly do tohoto implicitního sloupce. Chování funguje podobným způsobem jako u horizontálních směrů toku. <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výšku implicitního řádku z největšího podřízeného ovládacího prvku na řádku a všechny ukotvené nebo ukotvené podřízené ovládací prvky na tomto řádku jsou zarovnány nebo upraveny tak, aby odpovídaly předpokládanému řádku.

## <a name="example"></a>Příklad

Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je .<xref:System.Windows.Forms.FlowDirection.LeftToRight>

![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

Následující ilustrace znázorňuje čtyři tlačítka, která jsou ukotvená a ukotvená relativně k modrému tlačítku v <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je .<xref:System.Windows.Forms.FlowDirection.TopDown>

![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")

Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty <xref:System.Windows.Forms.Button> vlastností ovládacího prvku v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacím prvku.

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Přehled ovládacího prvku FlowLayoutPanel](flowlayoutpanel-control-overview.md)
