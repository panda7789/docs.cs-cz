---
title: 'Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040441"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře

Tabulková data jsou často prezentována ve formátu, ve kterém mají střídavé řádky odlišné barvy pozadí. Tento formát usnadňuje uživatelům informace o tom, které buňky jsou v jednotlivých řádcích, zejména u rozsáhlých tabulek, které mají mnoho sloupců.

<xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete zadat úplné informace o stylu pro střídavé řádky. K odlišení střídajících se řádků můžete použít vlastnosti stylu, jako je barva popředí a písmo, kromě barvy pozadí. Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.


### <a name="define-styles-for-alternating-rows"></a>Definovat styly pro střídavé řádky

1. <xref:System.Windows.Forms.DataGridView> Vyberte ovládací prvek v návrháři.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png)Studio.) vedle <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnosti.

3. V dialogovém okně **Tvůrce CellStyle** definujte styl nastavením vlastností a pomocí podokna **náhledu** potvrďte své volby. Styly, které zadáte, se použijí pro každý další řádek zobrazený v ovládacím prvku počínaje druhým.

4. Chcete-li definovat styly pro zbývající řádky, opakujte kroky 2 a 3 pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastnosti.

    > [!NOTE]
    > Buňky se zobrazují pomocí stylů děděných z více vlastností. Další informace o dědičnosti stylu naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Používání Návrháře s ovládacím prvkem Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
