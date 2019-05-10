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
ms.openlocfilehash: c14edebb7fd5ee133ce60769327e6b32dac1c7af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623711"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView
Při zobrazení funkce vstupní data pro uživatele máte často ověřit data do svého formuláře. <xref:System.Windows.Forms.DataGridView> Třída poskytuje pohodlný způsob, jak provádět ověřování předtím, než se zaměřuje na úložiště dat data. Data můžete ověřit pomocí manipulace <xref:System.Windows.Forms.DataGridView.CellValidating> událost, která je vyvolána <xref:System.Windows.Forms.DataGridView> při změně aktuální buňky.  
  
 V tomto podrobném návodu, načte řádky z `Customers` tabulky v ukázkové databázi Northwind a jejich zobrazení <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Když uživatel upraví buňky v `CompanyName` sloupce a pokouší se ponechte buňku, <xref:System.Windows.Forms.DataGridView.CellValidating> obslužná rutina události prozkoumá nový řetězec názvu společnosti k Ujistěte se, že je neprázdné; Pokud je nová hodnota je prázdný řetězec, <xref:System.Windows.Forms.DataGridView> zabrání uživatele kurzoru z něj odejít buňku, dokud nebude zadán neprázdný řetězec.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Ověřování dat v ovládacím prvku Windows Forms DataGridView](how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
- Přístup k serveru, která obsahuje ukázkovou databázi Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Ověření dat zadané v ovládacím prvku DataGridView  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku a <xref:System.Windows.Forms.BindingSource> komponenty.  
  
     Následující příklad kódu poskytuje základní inicializace a zahrnuje `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi.  
  
     Tento příklad kódu používá `GetData` metodu, která vrací mají údaj vyplněný <xref:System.Data.DataTable> objektu. Ujistěte se, že jste nastavili `connectionString` proměnných na hodnotu, která je vhodná pro vaši databázi.  
  
    > [!IMPORTANT]
    >  Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Použití ověřování Windows, označované také jako integrované zabezpečení, je bezpečnější způsob řízení přístupu k databázi. Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> a nastaví datovou vazbu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. Implementace obslužné rutiny pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellValidating> a <xref:System.Windows.Forms.DataGridView.CellEndEdit> události.  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> Obslužná rutina události je, kde můžete určit, zda je hodnota buňky v `CompanyName` sloupec je prázdný. Pokud se hodnota buňky ověření nezdaří, nastavte <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> třídu `true`. To způsobí, že <xref:System.Windows.Forms.DataGridView> ovládací prvek zabránit kurzor z něj odejít buňku. Nastavte <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> vlastnost na řádku, který má vysvětlující řetězec. Zobrazí se ikona chyby s popisem, který obsahuje text chyby. V <xref:System.Windows.Forms.DataGridView.CellEndEdit> nastavena obslužná rutina události, <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> vlastnost na řádku, který má prázdný řetězec. <xref:System.Windows.Forms.DataGridView.CellEndEdit> Dojde k události, pouze když buňku opustí režim úprav, což nelze provést, pokud selže ověření.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
- Kompilace a spuštění aplikace.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> naplněný daty z `Customers` tabulky. Když dvakrát kliknete na buňku `CompanyName` sloupce, můžete upravit její hodnotu. Pokud odstranění všech znaků a stisknutím klávesy tabulátor ukončete buňce <xref:System.Windows.Forms.DataGridView> zabraňuje ukončení. Když zadáte neprázdný řetězec do buňky, <xref:System.Windows.Forms.DataGridView> řízení umožňuje ukončete buňce.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku v několika ohledech:  
  
- Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [jak: Změna ohraničení a styly mřížky v Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Povolit nebo zakázat vstup uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md), a [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView – ovládací prvek](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Zkontrolujte chyby související s databáze uživatelský vstup. Další informace najdete v tématu [názorný postup: Zpracování chyb vzniklých při zadávání dat v Windows Forms DataGridView – ovládací prvek](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Zpracování velmi rozsáhlým datovým sadám pomocí virtuální režim. Další informace najdete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Přizpůsobení vzhledu buněk. Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [jak: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
