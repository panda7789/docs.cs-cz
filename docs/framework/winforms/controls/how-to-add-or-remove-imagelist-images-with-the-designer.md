---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: be17d5e6a12824c1c9edc867c99e77a6a1437a36
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658586"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře

Obrázky můžete přidat do <xref:System.Windows.Forms.ImageList> komponenty několika různými způsoby. Obrázky můžete přidat velmi rychle pomocí inteligentní značky přidružené <xref:System.Windows.Forms.ImageList>k, nebo Pokud nastavujete několik dalších vlastností <xref:System.Windows.Forms.ImageList>na, může být vhodnější přidat obrázky s okno Vlastnosti. Obrázky můžete také přidat pomocí kódu. Další informace o tom, jak přidat obrázky s kódem, naleznete [v tématu How to: Přidejte nebo odeberte obrázky s komponentou](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)model Windows Forms ImageList. Obvykle naplníte <xref:System.Windows.Forms.ImageList> komponentu obrázky předtím, než je přidružena k ovládacímu prvku, ale to není vyžadováno.

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Přidání nebo odebrání imagí pomocí okno Vlastnosti

1. <xref:System.Windows.Forms.ImageList> Vyberte součást nebo ji přidejte do formuláře.

2. V okno Vlastnosti klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png)Studio.) vedle <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti.

3. V **editoru kolekce imagí**klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Přidání nebo odebrání obrázků pomocí inteligentní značky

1. <xref:System.Windows.Forms.ImageList> Vyberte součást nebo ji přidejte do formuláře.

2. Klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")).

3. V dialogovém okně **úlohy ImageList** vyberte možnost **zvolit obrázky**.

4. V **editoru kolekce imagí** klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.

## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](../advanced/images-bitmaps-and-metafiles.md)
- [Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
