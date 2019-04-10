---
title: 'Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 6f36914387519b027fcf4cb6bf1e7654e551b3eb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328020"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel
Můžete zarovnání a roztažení ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> s <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-align-and-stretch-a-control"></a>Zarovnání a roztažení ovládacího prvku  
  
1. Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.  
  
2. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. <xref:System.Windows.Forms.Button> Ovládací prvek je uprostřed buňky.  
  
3. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left,Right`. <xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly šířka buňky.  
  
4. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top,Bottom`. <xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly výška buňky.  
  
5. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Ovládací prvek roztáhne a vyplní buňky.  
  
6. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Ovládací prvek vrátí na původní velikost a přesune do levého horního rohu buňky. **Návrháře formulářů Windows** nastavil <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.  
  
7. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Bottom,Right`. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune do pravého dolního rohu buňky.  
  
8. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune na střed buňku.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
