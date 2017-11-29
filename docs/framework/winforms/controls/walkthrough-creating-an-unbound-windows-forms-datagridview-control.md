---
title: "Návod: Vytvoření nepřipojeného ovládacího prvku Windows Forms DataGridView"
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
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2c57cfbab4d3af6cebff96517383999ae5b73d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Návod: Vytvoření nepřipojeného ovládacího prvku Windows Forms DataGridView
Často můžete chtít zobrazit tabulková data, která nepochází z databáze. Můžete například zobrazit obsah dvourozměrná pole řetězců. <xref:System.Windows.Forms.DataGridView> Třída poskytuje snadný a vysoce přizpůsobitelné způsob pro zobrazení dat bez vazby ke zdroji dat. Tento návod ukazuje, jak k naplnění <xref:System.Windows.Forms.DataGridView> řídit a spravovat přidávání a odstraňování řádků v režimu "nevázaný". Ve výchozím nastavení uživatel může přidávat nové řádky. Abyste zabránili přidávání řádků, nastavte <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost je `false`.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření nevázaný ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>K použití nepřipojeného ovládacího prvku DataGridView  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje následující deklarace proměnných a `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Implementace `SetupLayout` metoda v definici třídy svého formuláře k nastavení jeho rozložení.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Vytvoření `SetupDataGridView` metoda nastavit <xref:System.Windows.Forms.DataGridView> sloupce a vlastnosti.  
  
     Tato metoda nejprve přidá <xref:System.Windows.Forms.DataGridView> řízení formuláře <xref:System.Windows.Forms.Control.Controls%2A> kolekce. Počet sloupců, který se má zobrazit v dalším kroku se nastavuje pomocí <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> vlastnost. Nastavením je nastaven výchozí styl pro záhlaví sloupců <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, a <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> vrácené <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> vlastnost.  
  
     Jsou nastaveny vlastnosti rozložení a vzhled a poté jsou přiřazeny názvy sloupců. Když tato metoda ukončí, <xref:System.Windows.Forms.DataGridView> ovládací prvek je připraven k naplnit.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Vytvoření `PopulateDataGridView` metoda pro přidání řádků, které mají <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Každý řádek představuje skladbu a přidružené informace.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Pomocí metod nástroj na místě můžete připojit obslužné rutiny událostí.  
  
     Bude zpracovávat **přidat** a **odstranit** tlačítka se <xref:System.Windows.Forms.Control.Click> události, formuláře <xref:System.Windows.Forms.Form.Load> události a <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.  
  
     Když **přidat** tlačítka <xref:System.Windows.Forms.Control.Click> událost se vyvolá, nový, prázdný řádek přidán do <xref:System.Windows.Forms.DataGridView>.  
  
     Když **odstranit** tlačítka <xref:System.Windows.Forms.Control.Click> událost se vyvolá, se odstraní vybraný řádek, pokud je řádek pro nové záznamy, který uživateli umožňuje přidat nové řádky. Tento řádek je vždy poslední řádek v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Když formuláře <xref:System.Windows.Forms.Form.Load> událost se vyvolá, `SetupLayout`, `SetupDataGridView`, a `PopulateDataGridView` se nazývají pomocné metody.  
  
     Když <xref:System.Windows.Forms.DataGridView.CellFormatting> událost se vyvolá, jednotlivých buněk `Date` sloupec je formátován jako dlouhého data, pokud hodnota buňky nelze analyzovat.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí skladeb uvedené v `PopulateDataGridView`. Můžete přidat nové řádky s **přidat řádek** tlačítko a vy můžete odstranit vybrané řádky s **odstranit řádek** tlačítko. Nevázaný <xref:System.Windows.Forms.DataGridView> ovládací prvek je úložiště dat a jeho data jsou nezávislé na externí zdroj, například <xref:System.Data.DataSet> nebo pole.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> řízení několika způsoby:  
  
-   Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [postupy: Změna ohraničení a mřížky styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Povolit nebo zakázat vstupu uživatele na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [postupy: zabránění přidávání řádků a odstranění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), a [postup: Zkontrolujte sloupce jen pro čtení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Zkontrolujte chyby související s databáze uživatelský vstup. Další informace najdete v tématu [návod: zpracování chyb že dochází k při zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Zpracování pomocí virtuální režim velmi velkých datových sad. Další informace najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Přizpůsobení vzhledu buněk. Další informace najdete v tématu [postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) a [postupy: nastavení výchozí styly buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: vytvoření ovládacího prvku nevázaný Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
