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
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastností v jejích podřízených ovládacích prvků.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Chcete-li zarovnat podřízený ovládací prvek v buňce TableLayoutPanel  
  
1.  Vytvoření <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.  
  
2.  Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> a <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> vlastnosti, které chcete **1**.  
  
3.  Vytvoření <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. <xref:System.Windows.Forms.Button> Sídlí levém horním rohu buňky.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left`. <xref:System.Windows.Forms.Button> Řízení přesune vyrovnání levého okraje buňky.  
  
    > [!NOTE]
    >  Toto chování se liší od chování další ovládací prvky kontejneru. V další ovládací prvky kontejneru ovládacího prvku podřízené nepřesouvá při <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost nastavena a vzdálenost mezi ukotvené ovládacího prvku a hranic nadřazený kontejner vyřešen v době <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena.  
  
5.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`. <xref:System.Windows.Forms.Button> Řízení přesune tak, aby zabíral levém horním rohu buňky.  
  
6.  Opakujte krok 5 s hodnotou z `Top, Right` přesunout <xref:System.Windows.Forms.Button> řízení pravém horním rohu buňky. Opakování s hodnotami `Bottom, Left` a `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>K roztahování podřízený ovládací prvek v buňce TableLayoutPanel  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left, Right`. <xref:System.Windows.Forms.Button> Po změně velikosti k roztahování napříč buňky.  
  
    > [!NOTE]
    >  Toto chování se liší od chování další ovládací prvky kontejneru. V další ovládací prvky kontejneru podřízený ovládací prvek není při změně velikosti <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena na `Left, Right` nebo `Top, Bottom`.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom`. <xref:System.Windows.Forms.Button> Po změně velikosti k roztahování z horní části do dolní části buňky.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Po změně velikosti k vyplnění buňky.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `None`. <xref:System.Windows.Forms.Button> Změně velikosti nebo zarovnaný na střed v buňce ovládacího prvku.  
  
5.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Řízení přesune vyrovnání levého okraje buňky. <xref:System.Windows.Forms.Button> Ovládací prvek zachovává jeho šířka, ale jeho výšku se změnila velikost k vyplnění buňky svisle.  
  
    > [!NOTE]
    >  Toto je stejné chování, k níž dojde v další ovládací prvky kontejneru.  
  
6.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Po změně velikosti k vyplnění buňky.  
  
## <a name="example"></a>Příklad  
 Následující obrázek znázorňuje pět tlačítek ukotvené v pěti samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.  
  
 ![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Následující obrázek znázorňuje čtyři tlačítka ukotvené v rozích čtyři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.  
  
 ![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Následující obrázek znázorňuje tři tlačítka roztažen tak podle ukotvení v tři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buněk.  
  
 ![TableLayoutPanel – ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnoty vlastností <xref:System.Windows.Forms.Button> řídit ve <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
