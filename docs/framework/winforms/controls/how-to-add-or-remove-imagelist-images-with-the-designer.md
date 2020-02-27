---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628719"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře

Obrázky můžete přidat do <xref:System.Windows.Forms.ImageList> komponenty několika různými způsoby. Obrázky můžete přidat velmi rychle pomocí inteligentní značky přidružené k <xref:System.Windows.Forms.ImageList>, nebo Pokud nastavujete několik dalších vlastností <xref:System.Windows.Forms.ImageList>, může být vhodnější přidat obrázky s okno Vlastnosti. Obrázky můžete také přidat pomocí kódu. Další informace o tom, jak přidat obrázky s kódem, naleznete v tématu [How to: Add and Remove images with model Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). Obvykle naplníte <xref:System.Windows.Forms.ImageList> komponentu obrázky předtím, než je asociována s ovládacím prvkem, ale to není vyžadováno.

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Přidání nebo odebrání imagí pomocí okno Vlastnosti

1. Vyberte součást <xref:System.Windows.Forms.ImageList> nebo ji přidejte do formuláře.

2. V okno Vlastnosti klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ImageList.Images%2A>.

3. V **editoru kolekce imagí**klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Přidání nebo odebrání obrázků pomocí inteligentní značky

1. Vyberte součást <xref:System.Windows.Forms.ImageList> nebo ji přidejte do formuláře.

2. Klikněte na piktogram akcí návrháře (![Malá černá šipka](./media/designer-actions-glyph.gif))

3. V dialogovém okně **úlohy ImageList** vyberte možnost **zvolit obrázky**.

4. V **editoru kolekce imagí** klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.

## <a name="see-also"></a>Viz také

- [Obrázky, rastrové obrázky a metasoubory](../advanced/images-bitmaps-and-metafiles.md)
- [Návod: provádění běžných úloh pomocí akcí návrháře](perform-common-tasks-design-actions.md)
- [Komponenta ImageList](imagelist-component-windows-forms.md)
