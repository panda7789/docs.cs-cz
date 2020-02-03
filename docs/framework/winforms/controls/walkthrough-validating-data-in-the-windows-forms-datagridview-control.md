---
title: 'Návod: ověření dat v ovládacím prvku DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 45753fb206ad58616c9a727bd81bd2458db6053e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740101"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView

Když pro uživatele zobrazíte funkce pro zadávání dat, často je nutné ověřit data zadaná do formuláře. Třída <xref:System.Windows.Forms.DataGridView> poskytuje pohodlný způsob, jak provést ověření před tím, než se data odešlou do úložiště dat. Data můžete ověřit zpracováním události <xref:System.Windows.Forms.DataGridView.CellValidating>, která je vyvolána <xref:System.Windows.Forms.DataGridView> při změně aktuální buňky.

V tomto návodu načtete řádky z tabulky `Customers` v ukázkové databázi Northwind a zobrazíte je v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Když uživatel upraví buňku ve sloupci `CompanyName` a pokusí se ji opustit, obslužná rutina události <xref:System.Windows.Forms.DataGridView.CellValidating> ověří nový řetězec názvu společnosti, aby se zajistilo, že není prázdný. Pokud je nová hodnota prázdný řetězec, <xref:System.Windows.Forms.DataGridView> zabrání ukazateli na uživateli opustit tuto buňku, dokud nebude zadán neprázdný řetězec.

Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: Validate data v ovládacím prvku DataGridView model Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md).

## <a name="prerequisites"></a>Předpoklady

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Ověření dat zadaných v ovládacím prvku DataGridView

1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> komponentu.

    Následující příklad kódu poskytuje základní inicializaci a zahrnuje metodu `Main`.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.

    Tento příklad kódu používá metodu `GetData`, která vrací naplněný objekt <xref:System.Data.DataTable>. Ujistěte se, že jste nastavili proměnnou `connectionString` na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Použití ověřování systému Windows, označovaného také jako integrované zabezpečení, je bezpečnější způsob, jak řídit přístup k databázi. Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implementujte obslužné rutiny pro události <xref:System.Windows.Forms.DataGridView.CellValidating> a <xref:System.Windows.Forms.DataGridView.CellEndEdit> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.

    Obslužná rutina události <xref:System.Windows.Forms.DataGridView.CellValidating> je tam, kde určíte, zda je hodnota buňky ve sloupci `CompanyName` prázdná. Pokud hodnota buňky neprojde ověřením, nastavte vlastnost <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> třídy <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> na `true`. To způsobí, že ovládací prvek <xref:System.Windows.Forms.DataGridView> zabránit tomu, aby kurzor opustili buňku. Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> na řádku na vysvětlující řetězec. Tím se zobrazí ikona chyby s popisem, který obsahuje text chyby. V obslužné rutině události <xref:System.Windows.Forms.DataGridView.CellEndEdit> nastavte vlastnost <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> na řádku na prázdný řetězec. K události <xref:System.Windows.Forms.DataGridView.CellEndEdit> dojde pouze v případě, že buňka ukončuje režim úprav, který nemůže provést, pokud se ověření nezdařilo.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Zkompilujte a spusťte aplikaci.

  V tabulce `Customers` se zobrazí <xref:System.Windows.Forms.DataGridView> vyplněná daty. Když dvakrát kliknete na buňku ve sloupci `CompanyName`, můžete tuto hodnotu upravit. Pokud odstraníte všechny znaky a zaškrtnete klávesu TAB k ukončení buňky, <xref:System.Windows.Forms.DataGridView> zabráníte v ukončení. Když do buňky zadáte neprázdný řetězec, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám umožní tuto buňku ukončit.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o možnostech ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Vzhled a chování ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [Postup: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView model Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Povolí nebo zakáže vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [How to: zabránění přidání a odstranění řádku v ovládacím prvku datagridview model Windows Forms](prevent-row-addition-and-deletion-datagridview.md)a [Postupy: vytvoření sloupců jen pro čtení v ovládacím prvku model Windows Forms DataGridView](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Ověřte vstup uživatele o chybách souvisejících s databází. Další informace naleznete v tématu [Návod: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView model Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Přizpůsobení vzhledu buněk Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku model Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [Postupy: nastavení písma a barevných stylů v ovládacím prvku DataGridView model Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
