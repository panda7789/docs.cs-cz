---
title: Přidání tabulek a sloupců do ovládacího prvku DataGrid pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: fed7465fbe665b1945161653616e3a21640e0b2a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746260"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Data můžete zobrazit v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> v tabulkách a sloupcích vytvořením <xref:System.Windows.Forms.DataGridTableStyle> objektů a jejich přidáním do objektu <xref:System.Windows.Forms.GridTableStylesCollection>, který je k dispozici prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.TableStyles%2A>. Každý styl tabulky zobrazuje obsah libovolné tabulky dat, která je určena vlastností <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle>. Ve výchozím nastavení zobrazí styl tabulky bez zadaných stylů sloupců všechny sloupce v této tabulce dat. Můžete omezit, které sloupce z tabulky se zobrazí, přidáním <xref:System.Windows.Forms.DataGridColumnStyle> objektů do <xref:System.Windows.Forms.GridColumnStylesCollection>, ke kterému se dostanete prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> každého <xref:System.Windows.Forms.DataGridTableStyle>.

Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGrid>. Informace o tom, jak tento projekt nastavit, naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md). Ve výchozím nastavení v sadě Visual Studio 2005 není ovládací prvek <xref:System.Windows.Forms.DataGrid> v sadě **nástrojů**. Informace o jeho přidání naleznete v tématu [How to: Add Items to a panel nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Přidání tabulky do ovládacího prvku DataGrid v Návrháři

1. Aby bylo možné zobrazit data v tabulce, musíte nejprve vytvořit vazby ovládacího prvku <xref:System.Windows.Forms.DataGrid> k datové sadě. Další informace najdete v tématu [Postup: vytvoření vazby ovládacího prvku DataGrid model Windows Forms ke zdroji dat pomocí návrháře](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. V okno Vlastnosti vyberte vlastnost <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ovládacího prvku <xref:System.Windows.Forms.DataGrid> a potom klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti pro zobrazení **editoru kolekce styl DataGridTableStyle**.

3. V editoru kolekce klikněte na tlačítko **Přidat** a vložte tak styl tabulky.

4. Kliknutím na tlačítko **OK** zavřete Editor kolekce a poté jej znovu otevřete kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.

     Po opětovném otevření editoru kolekce se v rozevíracím seznamu zobrazí všechny datové tabulky svázané s ovládacím prvkem pro vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> stylu tabulky.

5. V poli **Členové** editoru kolekce klikněte na styl tabulky.

6. V poli **vlastnosti** editoru kolekce vyberte hodnotu <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> pro tabulku, kterou chcete zobrazit.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Přidání sloupce do ovládacího prvku DataGrid v Návrháři

1. V poli **Členové** v **editoru kolekce styl DataGridTableStyle**vyberte příslušný styl tabulky. V poli **vlastnosti** editoru kolekce vyberte kolekci <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> a potom klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti pro zobrazení **editoru kolekce styl DataGridColumnStyle**.

2. V editoru kolekce klikněte na tlačítko **Přidat** a vložte styl sloupce nebo klikněte na šipku dolů vedle položky **Přidat** a zadejte typ sloupce.

     V rozevíracím seznamu můžete vybrat buď typ <xref:System.Windows.Forms.DataGridTextBoxColumn> nebo <xref:System.Windows.Forms.DataGridBoolColumn>.

3. Kliknutím na OK zavřete **Editor kolekce styl DataGridColumnStyle**a pak ho znovu otevřete kliknutím na tlačítko se třemi tečkami vedle vlastnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

     Po opětovném otevření editoru kolekce se všechny sloupce dat v tabulce vázaných dat zobrazí v rozevíracím seznamu pro vlastnost <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> stylu sloupce.

4. V poli **Členové** editoru kolekce klikněte na styl sloupce.

5. V poli **vlastnosti** editoru kolekce vyberte hodnotu <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> pro sloupec, který chcete zobrazit.

## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
