---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987500"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Postupy: Ovládací prvky ukotvení na model Windows Forms

Pokud navrhujete formulář, který může uživatel změnit na velikost v době běhu, ovládací prvky ve formuláři by měly správně změnit velikost a změnit jejich polohu. Chcete-li změnit velikost ovládacích prvků dynamicky pomocí formuláře, můžete <xref:System.Windows.Forms.Control.Anchor%2A> použít vlastnost model Windows Forms ovládacích prvků. <xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost definuje pozici ukotvení ovládacího prvku. Když je ovládací prvek ukotven do formuláře a změní se velikost formuláře, ovládací prvek zachovává vzdálenost mezi ovládacím prvkem a polohou kotvy. Například pokud máte <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ukotven k levému, pravému a dolnímu okraji formuláře, <xref:System.Windows.Forms.TextBox> změní se velikost ovládacího prvku vodorovně, aby byla zachována stejná vzdálenost od pravé a levé strany formuláře. Kromě toho se ovládací prvek umístí svisle přímo tak, aby jeho poloha byla vždy stejná jako vzdálenost od spodního okraje ve formuláři. Pokud ovládací prvek není ukotven a dojde ke změně velikosti formuláře, poloha ovládacího prvku vztažena k okrajům formuláře je změněna.

<xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost komunikuje<xref:System.Windows.Forms.Control.AutoSize%2A> s vlastností. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Ukotvení ovládacího prvku na formuláři

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.

    > [!NOTE]
    > Můžete ukotvit více ovládacích prvků současně stisknutím klávesy CTRL, kliknutím na každý ovládací prvek ho vybrat a potom podle zbytku tohoto postupu.

2. V okně **vlastnosti** klikněte na šipku napravo od <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti.

     Zobrazí se editor, který zobrazuje více.

3. Chcete-li nastavit kotvu, klikněte na horní, levou, pravou nebo dolní část křížení.

     Ovládací prvky jsou ukotveny ve výchozím nastavení směrem nahoru a doleva.

4. Chcete-li vymazat stranu ovládacího prvku, který je ukotven, klikněte na něj ve vzájemném ramene.

5. Chcete-li <xref:System.Windows.Forms.Control.Anchor%2A> Editor vlastností zavřít, <xref:System.Windows.Forms.Control.Anchor%2A> klikněte znovu na název vlastnosti.

Když je formulář zobrazen v době běhu, změní se velikost ovládacího prvku tak, aby zůstala umístěná ve stejné vzdálenosti od okraje formuláře. Vzdálenost od ukotveného okraje vždy zůstane stejná jako vzdálenost definovaná při umístění ovládacího prvku do Návrhář formulářů.

> [!NOTE]
> Některé ovládací prvky, například <xref:System.Windows.Forms.ComboBox> ovládací prvek, mají omezení na jejich výšku. Ukotvení ovládacího prvku do dolní části jeho formuláře nebo kontejneru nemůže vynutit, aby ovládací prvek překročil limit výšky.

Zděděné ovládací prvky `Protected` musí být schopny být ukotveny. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho `Modifiers` vlastnost v okně **vlastnosti** .

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Ukotvit ovládací prvky na model Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md)
