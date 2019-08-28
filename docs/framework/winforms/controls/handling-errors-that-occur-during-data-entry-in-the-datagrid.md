---
title: 'Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046081"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView

Zpracování chyb z podkladového úložiště dat je požadovaná funkce pro aplikace pro zadávání dat. Model Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek usnadňuje vystavení <xref:System.Windows.Forms.DataGridView.DataError> události, která je vyvolána, když úložiště dat zjistí porušení omezení nebo přerušené obchodní pravidlo.

V tomto návodu navedete načtení řádků z `Customers` tabulky v ukázkové databázi Northwind a zobrazíte je <xref:System.Windows.Forms.DataGridView> v ovládacím prvku. Při zjištění duplicitní `CustomerID` hodnoty v novém řádku nebo upravovaném existujícím řádku <xref:System.Windows.Forms.DataGridView.DataError> dojde k události, která bude zpracována zobrazením <xref:System.Windows.Forms.MessageBox> , které popisuje výjimku.

Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Zpracovává chyby, ke kterým došlo při zadávání dat v ovládacím prvku](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView model Windows Forms.

## <a name="prerequisites"></a>Požadavky

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Zpracování chyb při zadávání dat v ovládacím prvku DataGridView

1. Vytvořte třídu, která je odvozena <xref:System.Windows.Forms.Form> z a <xref:System.Windows.Forms.DataGridView> obsahuje ovládací prvek a <xref:System.Windows.Forms.BindingSource> komponentu.

    Následující příklad kódu poskytuje základní inicializaci a obsahuje `Main` metodu.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.

    Tento příklad kódu používá `GetData` metodu, která vrací naplněný <xref:System.Data.DataTable> objekt. Ujistěte se, že jste nastavili `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.Form.Load> událost formuláře, která <xref:System.Windows.Forms.DataGridView> Inicializuje a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <xref:System.Windows.Forms.DataGridView.DataError> Zpracování události<xref:System.Windows.Forms.DataGridView>v.

    Pokud kontext pro chybu je operace potvrzení, zobrazí se chyba v <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Stisknutím klávesy F5 spusťte aplikaci.

  Zobrazí <xref:System.Windows.Forms.DataGridView> se ovládací prvek vyplněný daty z tabulky Customers. Pokud zadáte duplicitní hodnotu pro `CustomerID` a potvrdíte úpravu, hodnota buňky se vrátí automaticky a <xref:System.Windows.Forms.MessageBox> zobrazí se chyba, která zobrazí chybu zadání dat.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o <xref:System.Windows.Forms.DataGridView> schopnostech ovládacího prvku. Vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [jak: Změňte styly ohraničení a mřížky v ovládacím prvku](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView model Windows Forms.

- Povolí nebo zakáže vstup uživatele k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Další informace najdete v tématu [jak: Zabraňte přidávání a odstraňování řádků v ovládacím prvku](prevent-row-addition-and-deletion-datagridview.md)DataGridView model Windows Forms a [postupy: Zpřístupněte sloupce jen pro čtení v ovládacím prvku](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

- Ověřte vstup uživatele k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Další informace najdete v tématu [Návod: Ověřování dat v ovládacím prvku](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace najdete v tématu [Návod: Implementace virtuálního režimu v ovládacím prvku](implementing-virtual-mode-wf-datagridview-control.md)DataGridView model Windows Forms.

- Přizpůsobení vzhledu buněk Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku](customize-the-appearance-of-cells-in-the-datagrid.md) model Windows Forms DataGridView a [postup: Nastavte výchozí styly buňky pro ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView model Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Návod: Ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
