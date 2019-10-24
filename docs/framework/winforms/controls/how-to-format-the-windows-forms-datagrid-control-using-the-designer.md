---
title: 'Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: b3a85f5f9e51dae50a40058b8f07f92976da66f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "69666159"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Použití různých barev u různých částí <xref:System.Windows.Forms.DataGrid>ho ovládacího prvku může pomáhat usnadnit čtení a interpretaci informací. Barvu lze použít u řádků a sloupců. Řádky a sloupce můžete také skrýt nebo zobrazit podle vašeho uvážení.

Existují tři základní aspekty formátování <xref:System.Windows.Forms.DataGrid>ho ovládacího prvku:

- Můžete nastavit vlastnosti pro vytvoření výchozího stylu, ve kterém jsou zobrazena data.

- Z této základny pak můžete přizpůsobit způsob, jakým jsou v době běhu zobrazeny určité tabulky.

- Nakonec můžete upravit, které sloupce se zobrazí v datové mřížce, a také barvy a jiné zobrazené formátování.

Jako počáteční krok při formátování datové mřížky můžete nastavit vlastnosti samotného <xref:System.Windows.Forms.DataGrid>. Volby barev a formátů tvoří základ, ze kterého pak můžete provádět změny v závislosti na zobrazených tabulkách dat a sloupcích.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGrid>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md). V sadě Visual Studio 2005 není ovládací prvek <xref:System.Windows.Forms.DataGrid> ve výchozím nastavení součástí **sady nástrojů** . Další informace najdete v tématu [Postup: Přidání položek do sady nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Vytvoření výchozího stylu pro ovládací prvek DataGrid

1. Vyberte ovládací prvek <xref:System.Windows.Forms.DataGrid>.

2. V okně **vlastnosti** nastavte následující vlastnosti podle potřeby.

    |Vlastnost|Popis|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Vlastnost `BackColor` definuje barvu sudého číslování řádků mřížky. Když nastavíte vlastnost <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na jinou barvu, každý další řádek je nastaven na tuto novou barvu (řádky 1, 3, 5 atd.).|
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Barva pozadí sudého číslování řádků mřížky (řádky 0, 2, 4, 6 a tak dále).|
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Vzhledem k tomu, že vlastnosti <xref:System.Windows.Forms.DataGrid.BackColor%2A> a <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> určují barvu řádků v mřížce, vlastnost <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> Určuje barvu oblasti mimo oblast řádku, která je viditelná pouze v případě, že se mřížka posouvá do dolní části, nebo pokud je v seznamu uveden pouze pár řádků. mřížky.|
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl ohraničení mřížky, jedna z hodnot <xref:System.Windows.Forms.BorderStyle> výčtu.|
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Barva pozadí nadpisu okna mřížky, která se zobrazuje hned nad mřížkou|
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Písmo popisku v horní části mřížky|
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Barva pozadí nadpisu okna mřížky|
    |<xref:System.Windows.Forms.Control.Font%2A>|Písmo použité k zobrazení textu v mřížce|
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Barva písma zobrazeného v datech v řádcích datové mřížky|
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Barva čar mřížky pro datovou mřížku.|
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl čar, který odděluje buňky mřížky, jednu z hodnot výčtu <xref:System.Windows.Forms.DataGridLineStyle>.|
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Barva pozadí záhlaví řádků a sloupců|
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Písmo použité pro záhlaví sloupců|
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Barva popředí záhlaví sloupců v mřížce, včetně textu záhlaví sloupce a symbolů plus (+) a minus (-), které rozbalí a sbalí řádky, když se zobrazí více souvisejících tabulek.|
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Barva textu všech odkazů v mřížce dat, včetně odkazů na podřízené tabulky, název vztahu atd.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|V podřízené tabulce se jedná o barvu pozadí nadřazených řádků.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|V podřízené tabulce je to barva popředí nadřazených řádků.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Určuje, zda jsou názvy tabulek a sloupců zobrazeny v nadřazeném řádku prostřednictvím výčtu <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.|
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Výchozí šířka (v pixelech) sloupců v mřížce. Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Výška řádku (v pixelech) řádků v mřížce Tuto vlastnost nastavte před resetováním <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastností (buď samostatně, nebo prostřednictvím metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), nebo vlastnost nebude mít žádný vliv.<br /><br /> Vlastnost nemůže být nastavena na hodnotu menší než 0.|
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Šířka záhlaví řádků mřížky|
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu pozadí.|
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Když je vybrán řádek nebo buňka, jedná se o barvu popředí.|

    > [!NOTE]
    > Pokud přidáváte barvy ovládacích prvků, je možné nastavit, aby byl ovládací prvek nepřístupný z důvodu nedostatečné volby barvy (například Red a zeleně). K tomuto problému se vyhnete použitím barev dostupných na paletě **systémových barev** .

    Následující postup vyžaduje, aby byl ovládací prvek <xref:System.Windows.Forms.DataGrid> svázaný s datovou tabulkou. Další informace naleznete v tématu [How to: bind the model Windows Forms DataGrid Control to a Source (zdroj dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)).

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Nastavení stylu tabulky a sloupce tabulky dat v době návrhu

1. Ve formuláři vyberte ovládací prvek <xref:System.Windows.Forms.DataGrid>.

2. V okně **vlastnosti** vyberte vlastnost <xref:System.Windows.Forms.DataGrid.TableStyles%2A> a klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti tlačítko sady Visual Studio.](./media/visual-studio-ellipsis-button.png)).

3. V dialogovém okně **Editor kolekce styl DataGridTableStyle** klikněte na **Přidat** a přidejte do kolekce styl tabulky.

     Pomocí **editoru kolekce styl DataGridTableStyle**můžete přidat a odebrat styly tabulek, nastavit vlastnosti zobrazení a rozložení a nastavit název mapování pro styly tabulky.

4. Vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> nastavte na název mapování pro každý styl tabulky.

     Název mapování se používá k určení, který styl tabulky se má použít spolu s kterou tabulkou.

5. V **editoru kolekce styl DataGridTableStyle**vyberte vlastnost <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> a klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)).

6. V dialogovém okně **Editor kolekce styl DataGridColumnStyle** přidejte styly sloupců do stylu tabulky, který jste vytvořili.

     Pomocí **editoru kolekce styl DataGridColumnStyle**můžete přidat a odebrat styly sloupců, nastavit vlastnosti zobrazení a rozložení a nastavit název mapování a formátovací řetězce pro sloupce dat.

    > [!NOTE]
    > Další informace o formátování řetězců naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
