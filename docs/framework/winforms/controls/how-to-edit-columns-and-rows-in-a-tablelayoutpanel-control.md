---
title: 'Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 4473b20eea57088104a51eb1b6c080219223d214
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628641"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel

Editor kolekce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>, který se nazývá dialogové okno **styly sloupců a řádků** , lze použít k úpravě řádků a sloupců ovládacích prvků.

> [!NOTE]
> Chcete-li, aby byl ovládací prvek rozložen na více řádků nebo sloupců, nastavte `RowSpan` a vlastnosti `ColumnSpan` ovládacího prvku. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Pokud chcete ovládací prvek v rámci buňky zarovnat, nebo pokud chcete, aby se ovládací prvek roztáhnou v rámci buňky, použijte vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Úprava řádků a sloupců

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.

2. Klikněte na piktogram akcí návrháře <xref:System.Windows.Forms.TableLayoutPanel> (![malé černé šipky](./media/designer-actions-glyph.gif)) a výběrem možnosti **Upravit řádky a sloupce** otevřete dialogové okno **styly sloupců a řádků** . Můžete také kliknout pravým tlačítkem myši na ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> a vybrat možnost **Upravit řádky a sloupce** z místní nabídky.

3. Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z rozevíracího seznamu **typ člena** .

4. Chcete-li přidat nebo odebrat řádky, vyberte **řádky** v rozevíracím seznamu **typ člena** .

5. Kliknutím na tlačítko **Přidat** přidáte řádek nebo sloupec na konec seznamu **členů** .

6. Kliknutím na tlačítko **Vložit** přidáte řádek nebo sloupec před aktuálně vybranou položku v seznamu.

7. Pokud přidáváte řádek nebo sloupec, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.

8. Chcete-li odebrat řádek nebo sloupec, klikněte na tlačítko **Odebrat** a odstraňte aktuálně vybranou položku v seznamu **členů** .

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.SizeType>
- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
