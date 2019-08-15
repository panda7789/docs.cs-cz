---
title: 'Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 53faf31c8dd3be1606c491e95594c4aae5aedf98
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039676"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení výchozích stylů buňky a datových formátů pro ovládací prvek Windows Forms DataGridView pomocí Návrháře

<xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje zadat výchozí styly buňky a formáty dat buňky pro celý ovládací prvek, pro konkrétní sloupce, pro záhlaví řádků a sloupců a pro střídavé řádky pro vytvoření efektu hlavní knihy. Výchozí styly nastavené pro celý ovládací prvek jsou potlačeny výchozími styly nastavenými pro sloupce a střídavé řádky. Kromě toho styly, které jste nastavili v kódu pro jednotlivé řádky a buňky, přepíší výchozí styly.

Další informace o stylech buňky naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Chcete-li nastavit styly pro střídavé řádky, [Přečtěte si téma How to: Pomocí návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)nastavte střídavé styly řádků pro ovládací prvek DataGridView model Windows Forms.

Můžete také nastavit styly pomocí <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnosti tak, aby ovlivnily všechny řádky, které budou přidány do ovládacího prvku. Další informace o šabloně řádku naleznete v tématu [How to: K přizpůsobení řádků v ovládacím prvku](use-the-row-template-to-customize-rows-in-the-datagrid.md)DataGridView model Windows Forms použijte šablonu řádku.

Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.


### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Nastavení výchozích stylů pro všechny buňky v ovládacím prvku

1. <xref:System.Windows.Forms.DataGridView> Vyberte ovládací prvek v návrháři.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno vlastnosti](./media/visual-studio-ellipsis-button.png)sady Visual Studio) vedle <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>vlastnosti, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> . Zobrazí se dialogové okno **Tvůrce CellStyle** .

3. Definujte styl nastavením vlastností pomocí podokna **náhledu** a potvrďte své volby.

> [!NOTE]
> Pokud jsou povoleny vizuální styly, záhlaví řádků a sloupců (s výjimkou pro <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky upravena aktuálním motivem a <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> přepisují hodnoty vlastností <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> a.
>
> Můžete nastavit styly buněk pro více vybraných <xref:System.Windows.Forms.DataGridView> ovládacích prvků pomocí návrháře, ale pouze v případě, že mají stejné hodnoty jako vlastnost stylu buňky, kterou chcete upravit. Pokud se pro danou vlastnost liší žádné styly buněk, budou okna **vlastností** dialogového okna **Tvůrce CellStyle** prázdná.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Nastavení výchozích stylů pro buňky v jednotlivých sloupcích

1. Klikněte <xref:System.Windows.Forms.DataGridView> pravým tlačítkem myši na ovládací prvek v návrháři a vyberte možnost **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno vlastnosti](./media/visual-studio-ellipsis-button.png)sady Visual Studio) vedle <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnosti. Zobrazí se dialogové okno **Tvůrce CellStyle** .

4. Definujte styl nastavením vlastností pomocí podokna **náhledu** a potvrďte své volby.

### <a name="to-format-data-in-cells"></a>Formátování dat v buňkách

1. Použijte jeden z předchozích postupů k zobrazení dialogového okna **Tvůrce CellStyle** týkající se výchozí vlastnosti stylu buňky.

2. V dialogovém okně **Tvůrce CellStyle** klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png)Studio.) vedle <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> vlastnosti. Zobrazí se dialogové okno **řetězec formátu** .

3. Vyberte typ formátu a pak upravte podrobnosti o typu (například počet desetinných míst, která se mají zobrazit), pomocí pole **Ukázka** potvrďte své volby.

4. Pokud vytváříte vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku se zdrojem dat, který pravděpodobně obsahuje hodnoty null, vyplňte textové pole **hodnota null** . Tato hodnota se zobrazí, pokud je hodnota buňky rovna nulovému odkazu (`Nothing` v Visual Basic) nebo <xref:System.DBNull.Value?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
