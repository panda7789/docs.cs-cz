---
title: 'Postupy: Nastavení pořadí ovládacích prvků ve Windows Forms'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8a0a1c76b996f10de0ca963c5d8bdc2325a3f6b6
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987103"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Postupy: Nastavte pořadí ovládacích prvků na model Windows Forms

Pořadí prvků je pořadí, ve kterém uživatel přesune fokus z jednoho ovládacího prvku na jiný stisknutím klávesy TAB. Každý formulář má vlastní pořadí karet. Ve výchozím nastavení je pořadí karet stejné jako pořadí, ve kterém jste ovládací prvky vytvořili. Číslování pořadí karet začíná nulou.

## <a name="to-set-the-tab-order-of-a-control"></a>Nastavení pořadí prvků ovládacího prvku

1. V aplikaci Visual Studio v nabídce **zobrazení** vyberte **pořadí prvků**.

   Tím se aktivuje režim výběru pořadí karet na formuláři. Číslo (představující <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost) se zobrazí v levém horním rohu každého ovládacího prvku.

2. Chcete-li vytvořit požadované pořadí karet, klikněte na ovládací prvky postupně.

   > [!NOTE]
   > Místo na ovládacím prvku v pořadí prvků lze nastavit na libovolnou hodnotu větší nebo rovnou 0. Pokud dojde k duplicitě, je vyhodnocen pořadí vykreslování dvou ovládacích prvků a ovládací prvek nahoře je zobrazen na kartách jako první. (Pořadí vykreslování je vizuální vrstvení ovládacích prvků na formuláři podél osy z (hloubka) formuláře. Pořadí vykreslování určuje, které ovládací prvky jsou před dalšími ovládacími prvky.) Další informace o pořadí vykreslování naleznete v tématu [vrstvení Objects on model Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Po dokončení vyberte možnost **pořadí prvků** v nabídce **zobrazení** a nechejte tak režim pořadí tabulátoru.

   > [!NOTE]
   > Ovládací prvky, které nemohou získat fokus, a také zakázané a neviditelné ovládací prvky, <xref:System.Windows.Forms.Control.TabIndex%2A> nemají vlastnost a nejsou zahrnuty v pořadí prvků. Když uživatel stiskne klávesu TAB, tyto ovládací prvky se přeskočí.

Alternativně lze pořadí prvků nastavit v okno Vlastnosti pomocí <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnosti. <xref:System.Windows.Forms.Control.TabIndex%2A> Vlastnost ovládacího prvku určuje, kde je umístěn v pořadí prvků. Ve výchozím nastavení má <xref:System.Windows.Forms.Control.TabIndex%2A> první vykreslený ovládací prvek hodnotu 0, druhá <xref:System.Windows.Forms.Control.TabIndex%2A> má 1, a tak dále.

Kromě toho má <xref:System.Windows.Forms.GroupBox> ovládací prvek ve výchozím nastavení vlastní <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, což je celé číslo. Samotný <xref:System.Windows.Forms.GroupBox> ovládací prvek nemůže mít fokus v době běhu. Proto každý ovládací prvek v rámci <xref:System.Windows.Forms.GroupBox> má svou vlastní desítkovou <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, počínaje hodnotou. 0. Přirozeně, jako <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> u ovládacího prvku, se zvyšuje odpovídajícím způsobem ovládací prvky v rámci něj. Pokud jste změnili <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu z 5 na 6 <xref:System.Windows.Forms.Control.TabIndex%2A> , hodnota prvního ovládacího prvku v příslušné skupině se automaticky změní na 6,0 a tak dále.

Nakonec může být jakýkoli ovládací prvek mnoha na formuláři v pořadí prvků vynechán. Obvykle stisknutí klávesy TAB v době běhu vybere každý ovládací prvek v pořadí prvků. Vypnutím <xref:System.Windows.Forms.Control.TabStop%2A> vlastnosti můžete nastavit, aby byl ovládací prvek předán v pořadí prvků formuláře.

## <a name="to-remove-a-control-from-the-tab-order"></a>Odebrání ovládacího prvku z pořadí karet

V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost ovládacího prvku na **hodnotu false** .

Ovládací prvek, <xref:System.Windows.Forms.Control.TabStop%2A> jehož vlastnost byla nastavena tak `false` , aby nadále zachoval pozici v pořadí prvků, i když je ovládací prvek vynechán při cyklickém procházení ovládacími prvky pomocí klávesy TAB.

> [!NOTE]
> Skupina přepínačů má v době běhu jednu zarážku tabulátoru. Vybrané tlačítko (to znamená, že <xref:System.Windows.Forms.RadioButton.Checked%2A> tlačítko s vlastností nastavenou na `true`hodnotu) má svou <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost automaticky nastavenou `true`na hodnotu, zatímco ostatní tlačítka mají <xref:System.Windows.Forms.Control.TabStop%2A> svou vlastnost nastavenou na `false`. Další informace o ovládacích prvcích <xref:System.Windows.Forms.RadioButton> seskupení naleznete v tématu [seskupení model Windows Forms ovládací prvky RadioButton pro fungování jako sady](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Viz také:

- [Windows Forms – ovládací prvky](index.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
