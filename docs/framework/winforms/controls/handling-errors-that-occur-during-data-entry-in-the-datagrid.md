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
ms.openlocfilehash: 9e803b6450fb8c9ade4adde5bf98fb1c3c62c861
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313206"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView
Zpracování chyb z podkladové úložiště dat je požadované funkce pro zadávání dat aplikace. Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek umožňuje jednoduše zveřejněním <xref:System.Windows.Forms.DataGridView.DataError> událost, která se vyvolá, když zjistí úložiště dat porušení omezení nebo porušený obchodní pravidlo.  
  
 V tomto podrobném návodu, načte řádky z `Customers` tabulky v ukázkové databázi Northwind a jejich zobrazení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud duplicitní `CustomerID` zjištěna hodnota nový řádek nebo upravených existující řádek, <xref:System.Windows.Forms.DataGridView.DataError> dojde k události, která bude zpracována zobrazením <xref:System.Windows.Forms.MessageBox> , která popisuje výjimku.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Zpracování chyb, k nimž došlo při zadávání dat v Windows Forms DataGridView – ovládací prvek](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k serveru, která obsahuje ukázkovou databázi Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Pro zpracování chyb, zadávání dat v ovládacím prvku DataGridView  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku a <xref:System.Windows.Forms.BindingSource> komponenty.  
  
     Následující příklad kódu poskytuje základní inicializace a zahrnuje `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.  
  
     Tento příklad kódu používá `GetData` metodu, která vrací mají údaj vyplněný <xref:System.Data.DataTable> objektu. Ujistěte se, že jste nastavili `connectionString` proměnných na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3. Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4. Zpracování <xref:System.Windows.Forms.DataGridView.DataError> událostí na <xref:System.Windows.Forms.DataGridView>.  
  
     Pokud je kontext chyby operace potvrzení, zobrazit chybu v <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> ovládací prvek naplněný daty z tabulky Zákazníci. Pokud zadáte hodnotu pro duplicitní `CustomerID` a potvrdit úpravu, hodnota buňky se automaticky vrátí a zobrazí se <xref:System.Windows.Forms.MessageBox> , který se zobrazí chyba vstupní data.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku v několika ohledech:  
  
-   Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [jak: Změna ohraničení a styly mřížky v Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Povolit nebo zakázat vstup uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md), a [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView – ovládací prvek](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Ověření vstupu uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [názorný postup: Ověřování dat v Windows Forms DataGridView – ovládací prvek](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Zpracování velmi rozsáhlým datovým sadám pomocí virtuální režim. Další informace najdete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Přizpůsobení vzhledu buněk. Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [jak: Nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
