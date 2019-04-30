---
title: 'Návod: Vytvoření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView'
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
ms.openlocfilehash: a887dacfcb83b4b6ea4cb2690ab09b0d1b20b4fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772889"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView
Jeden z nejběžnějších scénářů pro použití <xref:System.Windows.Forms.DataGridView> je ovládací prvek *záznamů master/detail* formuláře, ve kterém se zobrazí nadřazené a podřízené vztah mezi dvěma tabulkami databáze. Výběr řádků v tabulce hlavní způsobí, že aktualizace pomocí odpovídající data podřízené tabulky.  
  
 Implementace hlavního/podrobného formuláře je snadný při použití interakce mezi <xref:System.Windows.Forms.DataGridView> ovládacího prvku a <xref:System.Windows.Forms.BindingSource> komponenty. V tomto návodu vytvoříte formuláře pomocí dvou <xref:System.Windows.Forms.DataGridView> ovládací prvky a dva <xref:System.Windows.Forms.BindingSource> komponenty. Na formuláři se zobrazí dvě související tabulky v ukázkové databázi Northwind SQL serveru: `Customers` a `Orders`. Až budete hotovi, budete mít formulář obsahující všechny zákazníky v databázi v hlavní <xref:System.Windows.Forms.DataGridView> a všech objednávek pro vybraného zákazníka do podrobností <xref:System.Windows.Forms.DataGridView>.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Vytvoření hlavního/podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
- Přístup k serveru, která obsahuje ukázkovou databázi Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-create-a-masterdetail-form"></a>K vytvoření hlavního/podrobného formuláře  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje dva <xref:System.Windows.Forms.DataGridView> ovládací prvky a dva <xref:System.Windows.Forms.BindingSource> komponenty. Následující kód obsahuje základní formulář inicializace a `Main` metody. Pokud použijete návrháře aplikace Visual Studio k vytvoření formuláře, můžete použít Návrháře generovaného kódu místo tento kód, ale je potřeba použít názvy uvedené v deklaracích proměnných tady.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi. V tomto příkladu `GetData` metodu, která naplní <xref:System.Data.DataSet> objekt, přidá <xref:System.Data.DataRelation> objektu do datové sady a vytvoří vazbu <xref:System.Windows.Forms.BindingSource> komponenty. Nezapomeňte nastavit `connectionString` proměnných na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3. Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která vytvoří vazbu <xref:System.Windows.Forms.DataGridView> ovládacích prvků do <xref:System.Windows.Forms.BindingSource> komponenty a volání `GetData` metody. Následující příklad zahrnuje kód, který změní velikost <xref:System.Windows.Forms.DataGridView> přizpůsobit zobrazených dat sloupce.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
- Kompilace a spuštění aplikace.  
  
     Zobrazí se dvě <xref:System.Windows.Forms.DataGridView> ovládací prvky, nad sebou. V horní části jsou zákazníci z Northwind `Customers` tabulky a v dolní části jsou `Orders` odpovídající k vybranému zákazníkovi. Když vyberete různé řádky v horním rohu <xref:System.Windows.Forms.DataGridView>, obsah nižší <xref:System.Windows.Forms.DataGridView> odpovídajícím způsobem měnit.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku v několika ohledech:  
  
- Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [jak: Změna ohraničení a styly mřížky v Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Povolit nebo zakázat vstup uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md), a [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView – ovládací prvek](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Ověření vstupu uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [názorný postup: Ověřování dat v Windows Forms DataGridView – ovládací prvek](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
- Zpracování velmi rozsáhlým datovým sadám pomocí virtuální režim. Další informace najdete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Přizpůsobení vzhledu buněk. Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [jak: Nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
