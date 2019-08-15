---
title: 'Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040298"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel

Můžete použít Editor <xref:System.Windows.Forms.TableLayoutPanel> kolekce ovládacího prvku, označovaný jako dialogové okno **styly sloupců a řádků** , chcete-li upravit řádky a sloupce ovládacích prvků.

> [!NOTE]
> Chcete-li, aby ovládací prvek zahrnoval více řádků nebo sloupců, nastavte `RowSpan` vlastnosti `ColumnSpan` a na ovládacím prvku. Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)TableLayoutPanel.
>
> Chcete-li zarovnat ovládací prvek v rámci buňky, nebo pokud chcete, aby se ovládací prvek roztáhl v rámci buňky, použijte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost ovládacího prvku. Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)TableLayoutPanel.

## <a name="to-edit-rows-and-columns"></a>Úprava řádků a sloupců

1. Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel>

2. ![](./media/vs-winformsmttagglyph.gif "") <xref:System.Windows.Forms.TableLayoutPanel> Klikněte na glyf inteligentních značek ovládacího prvku (VS_WinFormSmtTagGlyph glyf inteligentních značek) a vyberte **Upravit řádky a sloupce** . otevře se dialogové okno Styly sloupců a řádků. Můžete také kliknout <xref:System.Windows.Forms.TableLayoutPanel> pravým tlačítkem myši na ovládací prvek a vybrat možnost **Upravit řádky a sloupce** z místní nabídky.

3. Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z rozevíracího seznamu **typ člena** .

4. Chcete-li přidat nebo odebrat řádky, vyberte **řádky** v rozevíracím seznamu **typ člena** .

5. Kliknutím na tlačítko **Přidat** přidáte řádek nebo sloupec na konec seznamu **členů** .

6. Kliknutím na tlačítko **Vložit** přidáte řádek nebo sloupec před aktuálně vybranou položku v seznamu.

7. Pokud přidáváte řádek nebo sloupec, vyberte **typ velikosti** pro nový řádek nebo sloupec. Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.

8. Chcete-li odebrat řádek nebo sloupec, klikněte na tlačítko **Odebrat** a odstraňte aktuálně vybranou položku v seznamu **členů** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SizeType>
- [Ovládací prvek TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)
