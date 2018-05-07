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
ms.openlocfilehash: 8ad8caef5db13b1f917a6c27da523d3ded915d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView
Pokud má uživatelům zobrazit funkce vstupního datového, máte často ověřit data do svého formuláře. <xref:System.Windows.Forms.DataGridView> Třída poskytuje vhodný způsob k provedení ověření, než se zaměřuje na úložiště dat data. Data můžete ověřit pomocí zpracování <xref:System.Windows.Forms.DataGridView.CellValidating> událost, která je vyvolána <xref:System.Windows.Forms.DataGridView> až aktuální buňky změní.  
  
 V tomto návodu se budou načítat řádky z `Customers` tabulky v ukázkové databázi Northwind a jejich zobrazení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Když uživatel upravuje buňka v `CompanyName` sloupce a pokusí nechte buňky, <xref:System.Windows.Forms.DataGridView.CellValidating> obslužné rutiny události bude zkontrolujte nové řetězec názvu společnosti a ujistěte se, pokud nová hodnota je řetězec prázdný, je neprázdné; <xref:System.Windows.Forms.DataGridView> zabrání uživatele kurzoru mimo buňky, dokud nebude zadán neprázdný řetězec.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: ověření dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Přístup k serveru, který má ukázková databáze Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Ověřit data zadaná v ovládacím prvku DataGridView  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> řízení a <xref:System.Windows.Forms.BindingSource> součásti.  
  
     Následující příklad kódu poskytuje základní inicializace a zahrnuje `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  Implementujte metodu v definici třídy svého formuláře pro zpracování podrobnosti o připojení k databázi.  
  
     Tento příklad kódu používá `GetData` metodu, která vrátí vyplněná <xref:System.Data.DataTable> objektu. Ujistěte se, že jste nastavili `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Pomocí ověřování systému Windows, také známé jako integrované zabezpečení, je bezpečnější způsob, jak řídit přístup k databázi. Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastavuje datové vazby.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  Implementace obslužné rutiny pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellValidating> a <xref:System.Windows.Forms.DataGridView.CellEndEdit> události.  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> Obslužné rutiny události je, kde můžete určit, zda je hodnota buňky v `CompanyName` sloupec je prázdný. Pokud se ověření nezdaří hodnotu buňky, nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> třídy k `true`. To způsobí, že <xref:System.Windows.Forms.DataGridView> ovládací prvek, abyste zabránili nechat buňky kurzor. Nastavte <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> vlastnost na řádek, abyste vysvětlující řetězec. Zobrazí se ikona chyby s popisy, které obsahují text chyby. V <xref:System.Windows.Forms.DataGridView.CellEndEdit> nastavit popisovač události <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> vlastnost na řádku, který má prázdný řetězec. <xref:System.Windows.Forms.DataGridView.CellEndEdit> Události dojde, pouze když buňky ukončení režimu úprav, což nelze provést, pokud selže ověření.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Zkompilování a spuštění aplikace.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> , naplní se data z `Customers` tabulky. Po dvojitém kliknutí na buňku v `CompanyName` sloupec, můžete upravit hodnotu. Pokud odstraníte všechny znaky a stisknutím klávesy tabulátor ukončíte buňky, <xref:System.Windows.Forms.DataGridView> zabrání v ukončení. Když zadáte neprázdný řetězec do buňky, <xref:System.Windows.Forms.DataGridView> řízení umožňuje ukončit buňky.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> řízení několika způsoby:  
  
-   Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Povolit nebo zakázat vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [postupy: zabránění přidávání řádků a odstranění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), a [postup: Zkontrolujte sloupce jen pro čtení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Zkontrolujte chyby související s databáze uživatelský vstup. Další informace najdete v tématu [návod: zpracování chyb že dochází k při zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Zpracování pomocí virtuální režim velmi velkých datových sad. Další informace najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Přizpůsobení vzhledu buněk. Další informace najdete v tématu [postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) a [postupy: nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
