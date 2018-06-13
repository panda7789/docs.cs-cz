---
title: 'Návod: Vytvoření hlavního podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 38f7c6197fb3ee79119e41ab9620bc3aa2b21900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529438"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView
Jeden z nejběžnějších scénářů pro použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku *a podrobností* formuláře, ve kterém se zobrazí relaci nadřazený podřízený mezi dvěma tabulkami databáze. Výběr řádků v tabulce hlavní způsobí, že aktualizace s použitím dat odpovídající podřízené tabulky podrobností.  
  
 Implementace hlavního a podrobného formuláře je snadný při použití interakce mezi <xref:System.Windows.Forms.DataGridView> řízení a <xref:System.Windows.Forms.BindingSource> součásti. V tomto návodu vytvoříte formuláře pomocí dvou <xref:System.Windows.Forms.DataGridView> ovládací prvky a dvě <xref:System.Windows.Forms.BindingSource> součásti. Formulář se zobrazí dvě související tabulky v ukázkové databázi Northwind SQL Server: `Customers` a `Orders`. Jakmile budete hotovi, budete mít formulář, který zobrazuje všechny zákazníky v databázi v hlavní <xref:System.Windows.Forms.DataGridView> a všechny objednávky pro vybraného zákazníka. podrobně <xref:System.Windows.Forms.DataGridView>.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Přístup k serveru, který má ukázková databáze Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-create-a-masterdetail-form"></a>K vytvoření hlavního a podrobného formuláře  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky a dvě <xref:System.Windows.Forms.BindingSource> součásti. Následující kód poskytuje základní formuláře inicializace a zahrnuje `Main` metoda. Pokud použijete návrháře Visual Studio k vytvoření formuláře, můžete použít Návrháře generovaný kód místo tento kód, ale musíte použít názvy ukazuje deklarace proměnných sem.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Implementujte metodu v definici třídy svého formuláře pro zpracování podrobnosti připojení k databázi. Tento příklad používá `GetData` metoda, která naplní <xref:System.Data.DataSet> objektu, přidá <xref:System.Data.DataRelation> objektu do datové sady a vazby <xref:System.Windows.Forms.BindingSource> součásti. Nastavte `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která se váže <xref:System.Windows.Forms.DataGridView> prvky <xref:System.Windows.Forms.BindingSource> součásti a volání `GetData` metoda. Následující příklad obsahuje kód, který změní <xref:System.Windows.Forms.DataGridView> sloupců, aby vyhovovaly zobrazená data.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Zkompilování a spuštění aplikace.  
  
     Zobrazí se dvě <xref:System.Windows.Forms.DataGridView> prvky, nad sebou. V horní části jsou zákazníci z Northwind `Customers` tabulky a v dolní části jsou `Orders` odpovídající vybraného zákazníka. Při výběru různé řádky v horní <xref:System.Windows.Forms.DataGridView>, obsah dolní <xref:System.Windows.Forms.DataGridView> odpovídajícím způsobem.  
  
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
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
