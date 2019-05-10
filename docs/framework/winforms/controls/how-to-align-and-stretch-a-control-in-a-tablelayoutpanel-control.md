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
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210368"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel

Můžete zarovnání a roztažení ovládacích prvků <xref:System.Windows.Forms.TableLayoutPanel> s <xref:System.Windows.Forms.Control.Anchor%2A> a <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti.

## <a name="align-and-stretch-a-control"></a>Zarovnání a roztažení ovládacího prvku

1. V sadě Visual Studio, přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.

2. Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku. <xref:System.Windows.Forms.Button> Ovládací prvek je uprostřed buňky.

3. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Left,Right`. <xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly šířka buňky.

4. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top,Bottom`. <xref:System.Windows.Forms.Button> Řídit úsecích tak, aby odpovídaly výška buňky.

5. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Ovládací prvek roztáhne a vyplní buňky.

6. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Ovládací prvek vrátí na původní velikost a přesune do levého horního rohu buňky. **Návrháře formulářů Windows** nastavil <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Top, Left`.

7. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost `Bottom,Right`. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune do pravého dolního rohu buňky.

8. Nastavte hodnotu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Ovládacího prvku přesune na střed buňku.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
