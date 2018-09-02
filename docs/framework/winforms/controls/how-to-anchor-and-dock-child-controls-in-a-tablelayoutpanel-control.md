---
title: 'Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: ad09c30b2118a08f4249433c4f531e5bcef4acd5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418949"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Podporuje ovládací prvek <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti v jeho podřízených ovládacích prvků.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Chcete-li zarovnat podřízeného ovládacího prvku v buňce kontejneru TableLayoutPanel  
  
1.  Vytvoření <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.  
  
2.  Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> a <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> vlastností **1**.  
  
3.  Vytvoření <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. <xref:System.Windows.Forms.Button> Zabírá levém horním rohu buňky.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left`. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune na bylo v souladu s levého ohraničení buňky.  
  
    > [!NOTE]
    >  Toto chování se liší od chování další ovládací prvky kontejneru. V další ovládací prvky kontejneru podřízený ovládací prvek nepřesouvá při <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena a vzdálenost mezi ukotvené ovládacího prvku a hranice nadřazeného kontejneru je stanovena v době <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena.  
  
5.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune tak, aby obsadily levého horního rohu buňky.  
  
6.  Opakováním kroku 5 s hodnotou `Top, Right` přesunout <xref:System.Windows.Forms.Button> ovládacího prvku na pravém horním rohu buňky. Opakování s hodnotami `Bottom, Left` a `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Roztáhnout podřízeného ovládacího prvku v buňce kontejneru TableLayoutPanel  
  
1.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left, Right`. <xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku k roztahování v buňce.  
  
    > [!NOTE]
    >  Toto chování se liší od chování další ovládací prvky kontejneru. V další ovládací prvky kontejneru podřízený ovládací prvek není při změně velikosti <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena na `Left, Right` nebo `Top, Bottom`.  
  
2.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom`. <xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku k roztahování shora dolů buňce.  
  
3.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku tak, aby vyplnil buňku.  
  
4.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `None`. <xref:System.Windows.Forms.Button> Změně velikosti nebo na střed v buňce ovládacího prvku.  
  
5.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune na bylo v souladu s levého ohraničení buňky. <xref:System.Windows.Forms.Button> Uchovává šířku ovládacího prvku, ale jeho výška svou velikost tak, aby vyplnil buňky svisle.  
  
    > [!NOTE]
    >  Toto je stejné chování, který se nachází v jiné ovládací prvky kontejneru.  
  
6.  Změňte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Změně velikosti ovládacího prvku tak, aby vyplnil buňku.  
  
## <a name="example"></a>Příklad  
 Následující obrázek znázorňuje pět tlačítek ukotvené pět samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.  
  
 ![Kontejner TableLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Následující obrázek znázorňuje čtyři tlačítka ukotvené v rozích čtyři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.  
  
 ![Kontejner TableLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Následující obrázek znázorňuje tři tlačítka roztažená podle ukotvení tři samostatné <xref:System.Windows.Forms.TableLayoutPanel> buňky.  
  
 ![Kontejner TableLayoutPanel ukotvení](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnot vlastností pro <xref:System.Windows.Forms.Button> v ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření použijeme příklad z příkazového řádku pro visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
