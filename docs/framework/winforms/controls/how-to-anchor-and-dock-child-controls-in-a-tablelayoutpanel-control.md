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
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922824"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel
Ovládací prvek podporuje vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> a v jeho podřízených ovládacích prvcích. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Zarovnání podřízeného ovládacího prvku v buňce TableLayoutPanel  
  
1. Vytvořte na formuláři ovládací prvek. <xref:System.Windows.Forms.TableLayoutPanel>  
  
2. Nastavte hodnotu <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ovládacího prvku a vlastnosti na **1.** <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>  
  
3. Vytvoří ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Button> Zabírá levý horní roh buňky.  
  
4. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Left`. <xref:System.Windows.Forms.Button> Ovládací prvek se přesune k zarovnání s levým ohraničením buňky.  
  
    > [!NOTE]
    > Toto chování se liší od chování jiných ovládacích prvků kontejneru. V jiných ovládacích prvcích kontejneru se podřízený ovládací prvek nepřesouvá, když <xref:System.Windows.Forms.Control.Anchor%2A> je nastavena vlastnost a vzdálenost mezi ukotveným ovládacím prvkem a hranicí nadřazeného kontejneru je pevně nastavená v době, kdy <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena.  
  
5. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Left`. <xref:System.Windows.Forms.Button> Ovládací prvek se přesune, aby vybíral levý horní roh buňky.  
  
6. Opakujte krok 5 s hodnotou `Top, Right` pro <xref:System.Windows.Forms.Button> přesunutí ovládacího prvku do pravého horního rohu buňky. Opakujte s hodnotami `Bottom, Left` a `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Roztažení podřízeného ovládacího prvku v buňce TableLayoutPanel  
  
1. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Left, Right`. Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se roztáhla napříč buňkou.  
  
    > [!NOTE]
    > Toto chování se liší od chování jiných ovládacích prvků kontejneru. V jiných ovládacích prvcích kontejneru není podřízený ovládací prvek změněna velikost, pokud <xref:System.Windows.Forms.Control.Anchor%2A> je vlastnost nastavena na `Left, Right` nebo `Top, Bottom`.  
  
2. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Bottom`. Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se natáhla shora dolů v dolní části buňky.  
  
3. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `Top, Bottom, Left, Right`. Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se vyplnila buňka.  
  
4. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacího prvku na `None`. Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní na střed v buňce.  
  
5. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Ovládací prvek se přesune k zarovnání s levým ohraničením buňky. <xref:System.Windows.Forms.Button> Ovládací prvek si zachová šířku, ale jeho výška se změní tak, aby se buňka vyplnila svisle.  
  
    > [!NOTE]
    > Jedná se o stejné chování, ke kterému dochází v jiných ovládacích prvcích kontejneru.  
  
6. Změňte hodnotu <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Fill>. Velikost <xref:System.Windows.Forms.Button> ovládacího prvku se změní tak, aby se vyplnila buňka.  
  
## <a name="example"></a>Příklad  
 Následující ilustrace znázorňuje pět tlačítek ukotvených v pěti samostatných <xref:System.Windows.Forms.TableLayoutPanel> buňkách.  
  
 ![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Následující ilustrace znázorňuje čtyři tlačítka ukotvená v rozích čtyř samostatných <xref:System.Windows.Forms.TableLayoutPanel> buněk.  
  
 ![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Následující ilustrace znázorňuje tři tlačítka roztažená ukotvením ve třech samostatných <xref:System.Windows.Forms.TableLayoutPanel> buňkách.  
  
 ![Ukotvení kontejneru TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Následující příklad kódu ukazuje všechny kombinace <xref:System.Windows.Forms.Control.Anchor%2A> hodnot <xref:System.Windows.Forms.Button> vlastností ovládacího prvku v <xref:System.Windows.Forms.TableLayoutPanel> ovládacím prvku.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TableLayoutPanel>
- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
