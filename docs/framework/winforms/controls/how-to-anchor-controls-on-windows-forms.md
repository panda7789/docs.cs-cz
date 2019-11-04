---
title: 'Postupy: Ukotvování ovládacích prvků ve Windows Forms'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f12cb0d389344351c4ddf97ee9db37882de460
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459676"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Postupy: ukotvení ovládacích prvků na model Windows Forms

Pokud navrhujete formulář, který může uživatel změnit na velikost v době běhu, ovládací prvky ve formuláři by měly správně změnit velikost a změnit jejich polohu. Chcete-li změnit velikost ovládacích prvků dynamicky pomocí formuláře, můžete použít vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku model Windows Forms. Vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> definuje pozici ukotvení ovládacího prvku. Když je ovládací prvek ukotven do formuláře a změní se velikost formuláře, ovládací prvek zachovává vzdálenost mezi ovládacím prvkem a polohou kotvy. Například pokud máte ovládací prvek <xref:System.Windows.Forms.TextBox>, který je ukotven k levému, pravému a dolnímu okraji formuláře, při změně velikosti formuláře <xref:System.Windows.Forms.TextBox> ovládací prvek změní velikost vodorovně tak, aby se zachovala stejná vzdálenost od pravé a levé strany formuláře. Kromě toho se ovládací prvek umístí svisle přímo tak, aby jeho poloha byla vždy stejná jako vzdálenost od spodního okraje ve formuláři. Pokud ovládací prvek není ukotven a dojde ke změně velikosti formuláře, poloha ovládacího prvku vztažena k okrajům formuláře je změněna.

Vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> komunikuje s vlastností <xref:System.Windows.Forms.Control.AutoSize%2A>. Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).

## <a name="anchor-a-control-on-a-form"></a>Ukotvení ovládacího prvku na formuláři

1. V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.

    > [!NOTE]
    > Můžete ukotvit více ovládacích prvků současně stisknutím klávesy CTRL, kliknutím na každý ovládací prvek ho vybrat a potom podle zbytku tohoto postupu.

2. V okně **vlastnosti** klikněte na šipku napravo od vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A>.

     Zobrazí se editor, který zobrazuje více.

3. Chcete-li nastavit kotvu, klikněte na horní, levou, pravou nebo dolní část křížení.

     Ovládací prvky jsou ukotveny ve výchozím nastavení směrem nahoru a doleva.

4. Chcete-li vymazat stranu ovládacího prvku, který je ukotven, klikněte na něj ve vzájemném ramene.

5. Chcete-li zavřít editor vlastností <xref:System.Windows.Forms.Control.Anchor%2A>, klikněte znovu na název vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A>.

Když je formulář zobrazen v době běhu, změní se velikost ovládacího prvku tak, aby zůstala umístěná ve stejné vzdálenosti od okraje formuláře. Vzdálenost od ukotveného okraje vždy zůstane stejná jako vzdálenost definovaná při umístění ovládacího prvku do Návrhář formulářů.

> [!NOTE]
> Některé ovládací prvky, například ovládací prvek <xref:System.Windows.Forms.ComboBox>, mají omezení na jejich výšku. Ukotvení ovládacího prvku do dolní části jeho formuláře nebo kontejneru nemůže vynutit, aby ovládací prvek překročil limit výšky.

Zděděné ovládací prvky musí být `Protected`, aby je bylo možné ukotvit. Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho vlastnost `Modifiers` v okně **vlastnosti** .

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
- [Postupy: Vložení ovládacích prvků ve Windows Forms do doku](how-to-dock-controls-on-windows-forms.md)
- [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)
