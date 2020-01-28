---
title: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: ca602fa15e4648550bfa171a9c3abd057e930eca
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731367"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře

Ovládací prvek <xref:System.Windows.Forms.DataGridView> umožňuje zadat výchozí styly buňky a formáty dat buněk pro celý ovládací prvek, pro konkrétní sloupce, pro záhlaví řádků a sloupců a pro střídavé řádky pro vytvoření efektu hlavní knihy. Výchozí styly nastavené pro celý ovládací prvek jsou potlačeny výchozími styly nastavenými pro sloupce a střídavé řádky. Kromě toho styly, které jste nastavili v kódu pro jednotlivé řádky a buňky, přepíší výchozí styly.

Další informace o stylech buňky naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Chcete-li nastavit styly pro střídavé řádky, přečtěte si téma [Postup: nastavení stylů střídavých řádků pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).

Můžete také nastavit styly pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> pro vliv na všechny řádky, které budou přidány do ovládacího prvku. Další informace o šabloně řádku najdete v tématu [Postupy: použití šablony řádku k přizpůsobení řádků v ovládacím prvku DataGridView model Windows Forms](use-the-row-template-to-customize-rows-in-the-datagrid.md).

Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Nastavení výchozích stylů pro všechny buňky v ovládacím prvku

1. V návrháři vyberte ovládací prvek <xref:System.Windows.Forms.DataGridView>.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>. Zobrazí se dialogové okno **Tvůrce CellStyle** .

3. Definujte styl nastavením vlastností pomocí podokna **náhledu** a potvrďte své volby.

> [!NOTE]
> Pokud jsou povoleny vizuální styly, záhlaví řádků a sloupců (s výjimkou <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky upravena aktuálním motivem a přepisují hodnoty vlastností <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>.
>
> Můžete nastavit styly buněk pro více vybraných <xref:System.Windows.Forms.DataGridView> ovládacích prvků pomocí návrháře, ale pouze v případě, že mají stejné hodnoty jako vlastnost stylu buňky, kterou chcete upravit. Pokud se pro danou vlastnost liší žádné styly buněk, budou okna **vlastností** dialogového okna **Tvůrce CellStyle** prázdná.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Nastavení výchozích stylů pro buňky v jednotlivých sloupcích

1. V návrháři klikněte pravým tlačítkem myši na ovládací prvek <xref:System.Windows.Forms.DataGridView> a vyberte možnost **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>. Zobrazí se dialogové okno **Tvůrce CellStyle** .

4. Definujte styl nastavením vlastností pomocí podokna **náhledu** a potvrďte své volby.

### <a name="to-format-data-in-cells"></a>Formátování dat v buňkách

1. Použijte jeden z předchozích postupů k zobrazení dialogového okna **Tvůrce CellStyle** týkající se výchozí vlastnosti stylu buňky.

2. V dialogovém okně **Tvůrce CellStyle** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>. Zobrazí se dialogové okno **řetězec formátu** .

3. Vyberte typ formátu a pak upravte podrobnosti o typu (například počet desetinných míst, která se mají zobrazit), pomocí pole **Ukázka** potvrďte své volby.

4. Pokud vytváříte vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> ke zdroji dat, který pravděpodobně obsahuje hodnoty null, zadejte do textového pole **hodnota null** . Tato hodnota se zobrazí, pokud je hodnota buňky rovna nulovému odkazu (`Nothing` v Visual Basic) nebo v <xref:System.DBNull.Value?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
