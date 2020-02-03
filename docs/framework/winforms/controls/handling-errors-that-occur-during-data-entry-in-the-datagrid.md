---
title: 'Návod: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView'
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
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738736"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView

Zpracování chyb z podkladového úložiště dat je požadovaná funkce pro aplikace pro zadávání dat. Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGridView> usnadňuje vystavení události <xref:System.Windows.Forms.DataGridView.DataError>, která je vyvolána, když úložiště dat zjistí porušení omezení nebo poškozené obchodní pravidlo.

V tomto návodu načtete řádky z tabulky `Customers` v ukázkové databázi Northwind a zobrazíte je v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Pokud je v novém řádku nebo upravovaném existujícím řádkem zjištěna duplicitní `CustomerID` hodnota, dojde k události <xref:System.Windows.Forms.DataGridView.DataError>, která bude zpracována zobrazením <xref:System.Windows.Forms.MessageBox> popisujícího výjimku.

Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku model Windows Forms DataGridView](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).

## <a name="prerequisites"></a>Předpoklady

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Zpracování chyb při zadávání dat v ovládacím prvku DataGridView

1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> komponentu.

    Následující příklad kódu poskytuje základní inicializaci a zahrnuje metodu `Main`.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.

    Tento příklad kódu používá metodu `GetData`, která vrací naplněný objekt <xref:System.Data.DataTable>. Ujistěte se, že jste nastavili proměnnou `connectionString` na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Zpracování události <xref:System.Windows.Forms.DataGridView.DataError> v <xref:System.Windows.Forms.DataGridView>.

    Pokud je kontextem chyby operace potvrzení, zobrazí se chyba ve <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Stisknutím klávesy F5 spusťte aplikaci.

  Zobrazí se ovládací prvek <xref:System.Windows.Forms.DataGridView> vyplněný daty z tabulky Customers. Pokud zadáte duplicitní hodnotu pro `CustomerID` a potvrdíte úpravu, hodnota buňky se automaticky vrátí a zobrazí se <xref:System.Windows.Forms.MessageBox>, která zobrazí chybu zadání dat.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o možnostech ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Vzhled a chování ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [Postup: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView model Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Povolí nebo zakáže vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [How to: zabránění přidání a odstranění řádku v ovládacím prvku datagridview model Windows Forms](prevent-row-addition-and-deletion-datagridview.md)a [Postupy: vytvoření sloupců jen pro čtení v ovládacím prvku model Windows Forms DataGridView](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Ověří vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Přizpůsobení vzhledu buněk Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku model Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [Postup: nastavení výchozích stylů buňky pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
