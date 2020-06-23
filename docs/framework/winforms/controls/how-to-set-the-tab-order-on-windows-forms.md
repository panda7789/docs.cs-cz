---
title: Nastavení pořadí ovládacích prvků na kartě
description: Naučte se, jak nastavit pořadí ovládacích prvků na model Windows Forms. Nastavte pořadí ovládacích prvků pomocí sady Visual Studio nebo použijte vlastnost TabIndex v okno Vlastnosti.
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903356"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Postupy: nastavení pořadí ovládacích prvků na model Windows Forms

Pořadí prvků je pořadí, ve kterém uživatel přesune fokus z jednoho ovládacího prvku na jiný stisknutím klávesy TAB. Každý formulář má vlastní pořadí karet. Ve výchozím nastavení je pořadí karet stejné jako pořadí, ve kterém jste ovládací prvky vytvořili. Číslování pořadí karet začíná nulou.

## <a name="to-set-the-tab-order-of-a-control"></a>Nastavení pořadí prvků ovládacího prvku

1. V aplikaci Visual Studio v nabídce **zobrazení** vyberte **pořadí prvků**.

   Tím se aktivuje režim výběru pořadí karet na formuláři. Číslo (představující <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost) se zobrazí v levém horním rohu každého ovládacího prvku.

2. Chcete-li vytvořit požadované pořadí karet, klikněte na ovládací prvky postupně.

   > [!NOTE]
   > Místo na ovládacím prvku v pořadí prvků lze nastavit na libovolnou hodnotu větší nebo rovnou 0. Pokud dojde k duplicitě, je vyhodnocen pořadí vykreslování dvou ovládacích prvků a ovládací prvek nahoře je zobrazen na kartách jako první. (Pořadí vykreslování je vizuální vrstvení ovládacích prvků na formuláři podél osy z (hloubka) formuláře. Pořadí vykreslování určuje, které ovládací prvky jsou před dalšími ovládacími prvky.) Další informace o pořadí vykreslování naleznete v tématu [vrstvení Objects on model Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Po dokončení vyberte možnost **pořadí prvků** v nabídce **zobrazení** a nechejte tak režim pořadí tabulátoru.

   > [!NOTE]
   > Ovládací prvky, které nemohou získat fokus, a také zakázané a neviditelné ovládací prvky, nemají <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost a nejsou zahrnuty v pořadí prvků. Když uživatel stiskne klávesu TAB, tyto ovládací prvky se přeskočí.

Alternativně lze pořadí prvků nastavit v okno Vlastnosti pomocí <xref:System.Windows.Forms.Control.TabIndex%2A> Vlastnosti. <xref:System.Windows.Forms.Control.TabIndex%2A>Vlastnost ovládacího prvku určuje, kde je umístěn v pořadí prvků. Ve výchozím nastavení má první vykreslený ovládací prvek <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu 0, druhá má <xref:System.Windows.Forms.Control.TabIndex%2A> 1, a tak dále.

Kromě toho <xref:System.Windows.Forms.GroupBox> má ovládací prvek ve výchozím nastavení vlastní <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, což je celé číslo. <xref:System.Windows.Forms.GroupBox>Samotný ovládací prvek nemůže mít fokus v době běhu. Proto každý ovládací prvek v rámci <xref:System.Windows.Forms.GroupBox> má svou vlastní desítkovou <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, počínaje hodnotou. 0. Přirozeně, jako u <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> ovládacího prvku, se zvyšuje odpovídajícím způsobem ovládací prvky v rámci něj. Pokud jste změnili <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu z 5 na 6, <xref:System.Windows.Forms.Control.TabIndex%2A> hodnota prvního ovládacího prvku v příslušné skupině se automaticky změní na 6,0 a tak dále.

Nakonec může být jakýkoli ovládací prvek mnoha na formuláři v pořadí prvků vynechán. Obvykle stisknutí klávesy TAB v době běhu vybere každý ovládací prvek v pořadí prvků. Vypnutím <xref:System.Windows.Forms.Control.TabStop%2A> vlastnosti můžete nastavit, aby byl ovládací prvek předán v pořadí prvků formuláře.

## <a name="to-remove-a-control-from-the-tab-order"></a>Odebrání ovládacího prvku z pořadí karet

<xref:System.Windows.Forms.Control.TabStop%2A>V okně **vlastnosti** nastavte vlastnost ovládacího prvku na **hodnotu false** .

Ovládací prvek <xref:System.Windows.Forms.Control.TabStop%2A> , jehož vlastnost byla nastavena tak `false` , aby nadále zachoval pozici v pořadí prvků, i když je ovládací prvek vynechán při cyklickém procházení ovládacími prvky pomocí klávesy TAB.

> [!NOTE]
> Skupina přepínačů má v době běhu jednu zarážku tabulátoru. Vybrané tlačítko (to znamená, že tlačítko s <xref:System.Windows.Forms.RadioButton.Checked%2A> vlastností nastavenou na hodnotu `true` ) má svou <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost automaticky nastavenou na hodnotu `true` , zatímco ostatní tlačítka mají svou <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost nastavenou na `false` . Další informace o <xref:System.Windows.Forms.RadioButton> ovládacích prvcích seskupení naleznete v tématu [seskupení model Windows Forms ovládací prvky RadioButton pro fungování jako sady](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Viz také

- [Ovládací prvky model Windows Forms](index.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
