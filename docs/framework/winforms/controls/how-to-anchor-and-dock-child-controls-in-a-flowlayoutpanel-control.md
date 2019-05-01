---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 255ac50ae79d6931c9b82b50677c450c0834fdea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011179"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel
<xref:System.Windows.Forms.FlowLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti v jeho podřízených ovládacích prvků.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>A ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel  
  
1. Vytvoření <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na formuláři.  
  
2. Nastavte <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> mít pod kontrolou **300**a nastavte jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> k <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3. Pak vytvoříte další dva <xref:System.Windows.Forms.Button> ovládací prvky a umístit je <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
4. Nastavte <xref:System.Windows.Forms.Control.Width%2A> první tlačítka **200**.  
  
5. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhé tlačítko do <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  Na druhé tlačítko předpokládá stejnou šířku prvního tlačítka. Není roztáhnout na šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
6. Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost druhé tlačítko do `None`. To způsobí, že tlačítko předpokládat, že jeho původní šířka.  
  
7. Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost druhé tlačítko do `Left, Right`.  
  
    > [!IMPORTANT]
    >  Na druhé tlačítko předpokládá stejnou šířku prvního tlačítka. Není roztáhnout na šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Toto je obecné pravidlo pro ukotvení a dokování v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku: směrech svislé tok <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku implicitní sloupce z nejširší podřízený ovládací prvek ve sloupci. Všechny ostatní ovládací prvky v tomto sloupci se <xref:System.Windows.Forms.Control.Anchor%2A> nebo <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti jsou zarovnána, nebo roztažená do přizpůsobit tento sloupec implicitní. Chování funguje podobným způsobem jako směry vodorovné toku. <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výška implicitní řádek z nejvyšší podřízený ovládací prvek v řádku, a všechny ukotvené nebo ukotvené podřízené ovládací prvky v tomto řádku jsou zarovnána nebo velikostí podle předpokládané řádek.  
  
## <a name="example"></a>Příklad  
 Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotvena a ukotven vzhledem k modrého tlačítka v <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![Ukotvení FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotvena a ukotven vzhledem k modrého tlačítka v <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![Ukotvení FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnot vlastností pro <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Přehled ovládacího prvku FlowLayoutPanel](flowlayoutpanel-control-overview.md)
