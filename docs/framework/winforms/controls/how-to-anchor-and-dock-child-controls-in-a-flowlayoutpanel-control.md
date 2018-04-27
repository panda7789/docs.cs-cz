---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 183e9ea4a8451b3d1ed59aa5200dd4da22e50cf1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel
<xref:System.Windows.Forms.FlowLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastností v jejích podřízených ovládacích prvků.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel  
  
1.  Vytvoření <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek na formuláři.  
  
2.  Nastavte <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> řídit k **300**a nastavit jeho <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> k <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3.  Vytvořte dvě <xref:System.Windows.Forms.Button> ovládací prvky a umístěte je do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
4.  Nastavte <xref:System.Windows.Forms.Control.Width%2A> z na první tlačítko **200**.  
  
5.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na druhý tlačítko <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  Na druhé tlačítko předpokládá šířku stejné jako na první tlačítko. Není funkce stretch přes celou šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
6.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost na druhý tlačítko `None`. To způsobí, že tlačítko předpokládat, že původní šířku.  
  
7.  Nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost na druhý tlačítko `Left, Right`.  
  
    > [!IMPORTANT]
    >  Na druhé tlačítko předpokládá šířku stejné jako na první tlačítko. Není funkce stretch přes celou šířku <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku. Toto je obecná pravidla pro ukotvení a dokování v <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku: pro svislé toku pokynů <xref:System.Windows.Forms.FlowLayoutPanel> ovládací prvek vypočítá šířku sloupec odvozených z ovládacího prvku nejširší podřízené ve sloupci. Všechny ostatní ovládací prvky v tomto sloupci se <xref:System.Windows.Forms.Control.Anchor%2A> nebo <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti jsou zarovnána nebo roztažen tak, aby vyhovovaly předpokládané sloupce. Chování funguje podobným způsobem jako pro vodorovné toku pokynů. <xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek vypočítá výšku řádku odvozených z nejvyšší podřízený ovládací prvek řádek, a všechny ukotveného nebo ukotvené podřízených ovládacích prvků v tomto řádku jsou zarovnána nebo přizpůsobí předpokládané řádek.  
  
## <a name="example"></a>Příklad  
 Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotven a ukotven relativně k blue tlačítka na <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![FlowLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 Následující obrázek znázorňuje čtyři tlačítka, které jsou ukotven a ukotven relativně k blue tlačítka na <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Je <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![FlowLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 Následující příklad kódu ukazuje různé <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Přehled ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
