---
title: 'Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel'
description: Naučte se, jak používat dialogové okno Styly sloupců a řádků pro úpravu řádků a sloupců ovládacích prvků model Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619348"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel

Můžete použít Editor kolekce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, označovaný jako dialogové okno **styly sloupců a řádků** , chcete-li upravit řádky a sloupce ovládacích prvků.

> [!NOTE]
> Chcete-li, aby ovládací prvek zahrnoval více řádků nebo sloupců, nastavte `RowSpan` `ColumnSpan` vlastnosti a na ovládacím prvku. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Chcete-li zarovnat ovládací prvek v rámci buňky, nebo pokud chcete, aby se ovládací prvek roztáhl v rámci buňky, použijte vlastnost ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> . Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Úprava řádků a sloupců

1. Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek z **panelu nástrojů** do formuláře.

2. Klikněte na <xref:System.Windows.Forms.TableLayoutPanel> glyf akcí ovládacího prvku ( ![ malá černá šipka ](./media/designer-actions-glyph.gif) ) a vyberte **Upravit řádky a sloupce** . otevře se dialogové okno **styly sloupců a řádků** . Můžete také kliknout pravým tlačítkem myši na <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek a vybrat možnost **Upravit řádky a sloupce** z místní nabídky.

3. Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z rozevíracího seznamu **typ člena** .

4. Chcete-li přidat nebo odebrat řádky, vyberte **řádky** v rozevíracím seznamu **typ člena** .

5. Kliknutím na tlačítko **Přidat** přidáte řádek nebo sloupec na konec seznamu **členů** .

6. Kliknutím na tlačítko **Vložit** přidáte řádek nebo sloupec před aktuálně vybranou položku v seznamu.

7. Pokud přidáváte řádek nebo sloupec, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.

8. Chcete-li odebrat řádek nebo sloupec, klikněte na tlačítko **Odebrat** a odstraňte aktuálně vybranou položku v seznamu **členů** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel – ovládací prvek](tablelayoutpanel-control-windows-forms.md)
