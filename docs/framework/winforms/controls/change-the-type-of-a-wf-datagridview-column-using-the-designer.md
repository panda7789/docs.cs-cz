---
title: Změna typu sloupce DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628615"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít změnit typ sloupce, který již byl přidán do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>. Například můžete chtít upravit typy některých sloupců, které jsou generovány automaticky při svázání ovládacího prvku se zdrojem dat. To je užitečné v případě, že zobrazená tabulka obsahuje sloupce, které obsahují cizí klíče, do řádků v tabulce v relaci. V takovém případě možná budete chtít nahradit sloupce textového pole, které zobrazují tyto cizí klíče, sloupci pole se seznamem, které zobrazují smysluplnější hodnoty ze související tabulky.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Změna typu sloupce pomocí návrháře

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte vlastnost `ColumnType` na nový typ sloupce.

    > [!NOTE]
    > Vlastnost `ColumnType` je vlastnost pouze pro dobu návrhu, která označuje třídu reprezentující typ sloupce. Nejedná se o skutečnou vlastnost definovanou ve třídě Column.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
