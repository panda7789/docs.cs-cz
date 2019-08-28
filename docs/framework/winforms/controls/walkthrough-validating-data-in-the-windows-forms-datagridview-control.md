---
title: 'Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046383"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView

Když pro uživatele zobrazíte funkce pro zadávání dat, často je nutné ověřit data zadaná do formuláře. <xref:System.Windows.Forms.DataGridView> Třída nabízí pohodlný způsob, jak provést ověření před potvrzením dat do úložiště dat. Data lze ověřit zpracováním <xref:System.Windows.Forms.DataGridView.CellValidating> události, která je vyvolána <xref:System.Windows.Forms.DataGridView> při změně aktuální buňky.

V tomto návodu navedete načtení řádků z `Customers` tabulky v ukázkové databázi Northwind a zobrazíte je <xref:System.Windows.Forms.DataGridView> v ovládacím prvku. Když uživatel upraví buňku ve `CompanyName` sloupci a pokusí se ji opustit <xref:System.Windows.Forms.DataGridView.CellValidating> , obslužná rutina události ověří nový řetězec názvu společnosti, aby se zajistilo, že není prázdný. Pokud je nová hodnota prázdným řetězcem, <xref:System.Windows.Forms.DataGridView> zabrání se ukazateli uživatele. z buňky opustí, dokud nebude zadán neprázdný řetězec.

Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Ověří data v ovládacím prvku](how-to-validate-data-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

## <a name="prerequisites"></a>Požadavky

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Ověření dat zadaných v ovládacím prvku DataGridView

1. Vytvořte třídu, která je odvozena <xref:System.Windows.Forms.Form> z a <xref:System.Windows.Forms.DataGridView> obsahuje ovládací prvek a <xref:System.Windows.Forms.BindingSource> komponentu.

    Následující příklad kódu poskytuje základní inicializaci a obsahuje `Main` metodu.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.

    Tento příklad kódu používá `GetData` metodu, která vrací naplněný <xref:System.Data.DataTable> objekt. Ujistěte se, že jste nastavili `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Použití ověřování systému Windows, označovaného také jako integrované zabezpečení, je bezpečnější způsob, jak řídit přístup k databázi. Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.Form.Load> událost formuláře, která <xref:System.Windows.Forms.DataGridView> Inicializuje a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implementujte obslužné rutiny <xref:System.Windows.Forms.DataGridView> pro <xref:System.Windows.Forms.DataGridView.CellValidating> události <xref:System.Windows.Forms.DataGridView.CellEndEdit> ovládacího prvku a.

    Obslužná rutina `CompanyName`událostije tam, kde určíte, zda je hodnota buňky ve sloupci prázdná. <xref:System.Windows.Forms.DataGridView.CellValidating> Pokud hodnota buňky neprojde ověřením, nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> třídy na `true`. To způsobí, <xref:System.Windows.Forms.DataGridView> že ovládací prvek zabrání ukazateli opustit buňku. <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> Nastavte vlastnost na řádku na vysvětlující řetězec. Tím se zobrazí ikona chyby s popisem, který obsahuje text chyby. V obslužné rutině <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>událostinastavte vlastnost na řádku na prázdný řetězec. <xref:System.Windows.Forms.DataGridView.CellEndEdit> K <xref:System.Windows.Forms.DataGridView.CellEndEdit> události dojde pouze v případě, že buňka ukončuje režim úprav, kterou nemůže provést, pokud se ověření nezdařilo.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Zkompilujte a spusťte aplikaci.

  V `Customers` tabulce se zobrazí <xref:System.Windows.Forms.DataGridView> vyplněná data. Když dvakrát kliknete na buňku ve `CompanyName` sloupci, můžete tuto hodnotu upravit. Pokud odstraníte všechny znaky a zaškrtnete klávesu TAB, zabráníte tím ukončení <xref:System.Windows.Forms.DataGridView> této buňky. Když do buňky zadáte neprázdný řetězec, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám umožní ukončit tuto buňku.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o <xref:System.Windows.Forms.DataGridView> schopnostech ovládacího prvku. Vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [jak: Změňte styly ohraničení a mřížky v ovládacím prvku](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView model Windows Forms.

- Povolí nebo zakáže vstup uživatele k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Další informace najdete v tématu [jak: Zabraňte přidávání a odstraňování řádků v ovládacím prvku](prevent-row-addition-and-deletion-datagridview.md)DataGridView model Windows Forms a [postupy: Zpřístupněte sloupce jen pro čtení v ovládacím prvku](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

- Ověřte vstup uživatele o chybách souvisejících s databází. Další informace najdete v tématu [Návod: Zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView model Windows Forms.

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace najdete v tématu [Návod: Implementace virtuálního režimu v ovládacím prvku](implementing-virtual-mode-wf-datagridview-control.md)DataGridView model Windows Forms.

- Přizpůsobení vzhledu buněk Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku](customize-the-appearance-of-cells-in-the-datagrid.md) model Windows Forms DataGridView a [postup: Nastavte styly písma a barev v ovládacím prvku](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Ověřit data v ovládacím prvku DataGridView model Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Návod: Zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku model Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
