---
title: "Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 016a30e4b578ead199124d70cc12f240c74bf370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView
Zpracování chyb z podkladové úložiště dat je povinnou funkci pro zadávání dat aplikace. Windows Forms <xref:System.Windows.Forms.DataGridView> řízení to výrazně usnadňuje díky zpřístupnění <xref:System.Windows.Forms.DataGridView.DataError> událost, která se vyvolá, když zjistí úložiště dat porušení omezení nebo přerušená obchodní pravidlo.  
  
 V tomto návodu se budou načítat řádky z `Customers` tabulky v ukázkové databázi Northwind a jejich zobrazení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud duplicitní `CustomerID` hodnota je zjištěn během nového řádku nebo upravených stávající řádek, <xref:System.Windows.Forms.DataGridView.DataError> události dojde, který bude zpracován adresou zobrazení <xref:System.Windows.Forms.MessageBox> která popisuje výjimku.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: zpracování chyb, dojít během zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Přístup k serveru, který má ukázková databáze Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Zpracování chyb zadávání dat v ovládacím prvku DataGridView  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> řízení a <xref:System.Windows.Forms.BindingSource> součásti.  
  
     Následující příklad kódu poskytuje základní inicializace a zahrnuje `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  Implementujte metodu v definici třídy svého formuláře pro zpracování podrobnosti o připojení k databázi.  
  
     Tento příklad kódu používá `GetData` metodu, která vrátí vyplněná <xref:System.Data.DataTable> objektu. Ujistěte se, že jste nastavili `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastavuje datové vazby.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  Zpracování <xref:System.Windows.Forms.DataGridView.DataError> událostí na <xref:System.Windows.Forms.DataGridView>.  
  
     Pokud je kontext chyby operace potvrzení, zobrazí chybu v <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> řízení, naplní se data z tabulky zákazníků. Pokud zadáte hodnotu duplicitní pro `CustomerID` a Potvrdit úpravy, bude automaticky vracet hodnotu buňky a zobrazí se <xref:System.Windows.Forms.MessageBox> , zobrazí se chyba vstupní data.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> řízení několika způsoby:  
  
-   Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Povolit nebo zakázat vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [postupy: zabránění přidávání řádků a odstranění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), a [postup: Zkontrolujte sloupce jen pro čtení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Ověření vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [návod: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Zpracování pomocí virtuální režim velmi velkých datových sad. Další informace najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Přizpůsobení vzhledu buněk. Další informace najdete v tématu [postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) a [postupy: nastavení výchozí styly buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
