---
title: 'Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210371"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu

Zarovnat na hranici formulářů tím, že nastavíte hodnotu ovládacího prvku můžete provést <xref:System.Windows.Forms.Control.Dock%2A> vlastnost. Tato vlastnost určuje, kde se nachází váš ovládací prvek ve formuláři. <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:

|Nastavení|Vliv na váš ovládací prvek|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Ukotví do dolní části formuláře.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Vyplní veškerý zbývající prostor ve formuláři.|
|<xref:System.Windows.Forms.DockStyle.Left>|Ukotví na levou stranu formuláře.|
|<xref:System.Windows.Forms.DockStyle.None>|Fakturuje se u není dock kdekoli a zobrazí se v umístění určeném jeho <xref:System.Windows.Forms.Control.Location%2A>.|
|<xref:System.Windows.Forms.DockStyle.Right>|Ukotví na pravou stranu formuláře.|
|<xref:System.Windows.Forms.DockStyle.Top>|Ukotví do horní části formuláře.|

Tyto hodnoty můžete také nastavit v kódu. Další informace najdete v tématu [jak: Zarovnání ovládacího prvku k okrajům formulářů](how-to-align-a-control-to-the-edges-of-forms.md).

## <a name="set-the-dock-property-for-your-control-at-design-time"></a>Nastavení vlastnosti Dock ovládacího prvku v době návrhu

1. V Návrháři formulářů Windows v sadě Visual Studio vyberte ovládací prvek.

2. V **vlastnosti** okna, klikněte na tlačítko Další pole rozevíracího seznamu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.

     Grafické rozhraní představující šest možných <xref:System.Windows.Forms.Control.Dock%2A> nastavení se zobrazí.

3. Vyberte příslušné nastavení.

4. Ovládací prvek bude nyní ukotvit způsobem popsaným v nastavení.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Postupy: Zarovnání ovládacího prvku k okrajům formulářů](how-to-align-a-control-to-the-edges-of-forms.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Postupy: Ukotvení ovládacích prvků ve Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
