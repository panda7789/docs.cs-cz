---
title: 'Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040041"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Můžete zobrazit data v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> v tabulkách a sloupcích vytvořením <xref:System.Windows.Forms.DataGridTableStyle> objektů <xref:System.Windows.Forms.GridTableStylesCollection> a jejich přidáním do objektu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> , který je k dispozici prostřednictvím <xref:System.Windows.Forms.DataGrid> vlastnosti ovládacího prvku. Každý styl tabulky zobrazuje obsah libovolné tabulky dat, která je určena ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnosti. <xref:System.Windows.Forms.DataGridTableStyle> Ve výchozím nastavení zobrazí styl tabulky bez zadaných stylů sloupců všechny sloupce v této tabulce dat. Můžete omezit, které sloupce z <xref:System.Windows.Forms.DataGridColumnStyle> tabulky se zobrazí přidáním objektů <xref:System.Windows.Forms.GridColumnStylesCollection>do objektu, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> který je k dispozici prostřednictvím vlastnosti každého <xref:System.Windows.Forms.DataGridTableStyle>.

Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGrid> ovládací prvek. Informace o tom, jak tento projekt nastavit, naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms. Ve výchozím nastavení v sadě Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> není ovládací prvek v sadě **nástrojů**. Informace o jeho přidání naleznete v tématu [How to: Přidejte položky do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Přidání tabulky do ovládacího prvku DataGrid v Návrháři

1. Aby bylo možné zobrazit data v tabulce, je nutné nejprve navazovat <xref:System.Windows.Forms.DataGrid> ovládací prvek na datovou sadu. Další informace najdete v tématu [jak: Navažte model Windows Forms ovládací prvek DataGrid ke zdroji dat pomocí návrháře](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. ![](./media/visual-studio-ellipsis-button.png)Vyberte vlastnost <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.TableStyles%2A> ovládacího prvku v okno Vlastnosti a potom klikněte na tlačítko se třemi tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.) vedle vlastnosti pro zobrazení **Editor kolekce styl DataGridTableStyle**

3. V editoru kolekce klikněte na tlačítko **Přidat** a vložte tak styl tabulky.

4. Kliknutím na tlačítko **OK** zavřete Editor kolekce a poté jej znovu otevřete kliknutím na tlačítko se třemi tečkami vedle <xref:System.Windows.Forms.DataGrid.TableStyles%2A> vlastnosti.

     Po opětovném otevření editoru kolekce se v rozevíracím seznamu zobrazí všechny datové tabulky svázané s ovládacím prvkem pro <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost stylu tabulky.

5. V poli **Členové** editoru kolekce klikněte na styl tabulky.

6. V poli **vlastnosti** editoru kolekce vyberte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> hodnotu pro tabulku, kterou chcete zobrazit.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Přidání sloupce do ovládacího prvku DataGrid v Návrháři

1. V poli **Členové** v **editoru kolekce styl DataGridTableStyle**vyberte příslušný styl tabulky. V poli **vlastnosti** editoru kolekce vyberte <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekci a potom klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti na Zobrazte **Editor kolekce styl DataGridColumnStyle**.

2. V editoru kolekce klikněte na tlačítko **Přidat** a vložte styl sloupce nebo klikněte na šipku dolů vedle položky **Přidat** a zadejte typ sloupce.

     V rozevíracím seznamu můžete vybrat buď <xref:System.Windows.Forms.DataGridTextBoxColumn> typ, nebo. <xref:System.Windows.Forms.DataGridBoolColumn>

3. Kliknutím na OK zavřete **Editor kolekce styl DataGridColumnStyle**a pak ho znovu otevřete kliknutím na tlačítko se třemi tečkami vedle <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> vlastnosti.

     Po opětovném otevření editoru kolekce se všechny sloupce dat v tabulce vázaných dat zobrazí v rozevíracím seznamu pro <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> vlastnost stylu sloupce.

4. V poli **Členové** editoru kolekce klikněte na styl sloupce.

5. V poli **vlastnosti** editoru kolekce vyberte <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> hodnotu pro sloupec, který chcete zobrazit.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
