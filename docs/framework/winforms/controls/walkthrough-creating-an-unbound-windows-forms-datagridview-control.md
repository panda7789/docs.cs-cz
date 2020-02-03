---
title: Vytvoření nevázaného ovládacího prvku DataGridView
ms.date: 03/30/2017
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
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740176"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Návod: Vytvoření nepřipojeného ovládacího prvku Windows Forms DataGridView
Často je vhodné zobrazit tabulková data, která nepocházejí z databáze. Například může být vhodné zobrazit obsah dvojrozměrného pole řetězců. Třída <xref:System.Windows.Forms.DataGridView> poskytuje snadný a vysoce přizpůsobitelný způsob zobrazení dat bez vazby na zdroj dat. Tento návod ukazuje, jak naplnit ovládací prvek <xref:System.Windows.Forms.DataGridView> a spravovat přidávání a odstraňování řádků v režimu "bez vazby". Ve výchozím nastavení může uživatel přidat nové řádky. Chcete-li zabránit přidání řádků, nastavte vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> je `false`.  
  
 Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: Create a Unbound model Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Použití ovládacího prvku nevázané DataGridView  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje následující deklarace proměnných a metodu `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implementací metody `SetupLayout` v definici třídy formuláře nastavte rozložení formuláře.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Vytvořte metodu `SetupDataGridView` pro nastavení <xref:System.Windows.Forms.DataGridView> sloupců a vlastností.  
  
     Tato metoda nejprve přidá ovládací prvek <xref:System.Windows.Forms.DataGridView> do kolekce <xref:System.Windows.Forms.Control.Controls%2A> formuláře. V dalším kroku se počet zobrazených sloupců nastaví pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.ColumnCount%2A>. Výchozí styl záhlaví sloupců je nastaven nastavením vlastností <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>a <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> vrácených vlastností <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>.  
  
     Vlastnosti rozložení a vzhledu jsou nastaveny a pak se přiřazují názvy sloupců. Po ukončení této metody je ovládací prvek <xref:System.Windows.Forms.DataGridView> připraven k naplnění.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Vytvořte metodu `PopulateDataGridView` pro přidání řádků do ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
     Každý řádek představuje skladbu a její přidružené informace.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. V případě, že jsou k dismístě podpůrné metody, můžete připojit obslužné rutiny událostí.  
  
     Budete zpracovávat tlačítka **Přidat** a **Odstranit** <xref:System.Windows.Forms.Control.Click> události, událost <xref:System.Windows.Forms.Form.Load> formuláře a událost <xref:System.Windows.Forms.DataGridView.CellFormatting> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
     Když se aktivuje událost <xref:System.Windows.Forms.Control.Click> tlačítka **Přidat** , do <xref:System.Windows.Forms.DataGridView>se přidá nový prázdný řádek.  
  
     Když je vyvolána událost <xref:System.Windows.Forms.Control.Click> tlačítka **Odstranit** , je vybraný řádek odstraněn, pokud se nejedná o řádek pro nové záznamy, který uživateli umožňuje přidat nové řádky. Tento řádek je vždy posledním řádkem v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.  
  
     Když je vyvolána událost <xref:System.Windows.Forms.Form.Load> formuláře, jsou volána `SetupLayout`, `SetupDataGridView`a metody nástrojů `PopulateDataGridView`.  
  
     Když je vyvolána událost <xref:System.Windows.Forms.DataGridView.CellFormatting>, jsou všechny buňky ve sloupci `Date` formátovány jako dlouhé datum, pokud hodnotu buňky nelze analyzovat.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Testování formuláře  
  
- Stisknutím klávesy F5 spusťte aplikaci.  
  
     Zobrazí se ovládací prvek <xref:System.Windows.Forms.DataGridView>, který zobrazuje skladby uvedené v `PopulateDataGridView`. Můžete přidat nové řádky pomocí tlačítka **Přidat řádek** a vybrané řádky můžete odstranit pomocí tlačítka **Odstranit řádek** . Nevázaný ovládací prvek <xref:System.Windows.Forms.DataGridView> je úložiště dat a jeho data jsou nezávislá na jakémkoli externím zdroji, jako je například <xref:System.Data.DataSet> nebo pole.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace vám poskytne základní informace o možnostech ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Vzhled a chování ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit několika způsoby:  
  
- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [Postup: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView model Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Povolí nebo zakáže vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [How to: zabránění přidání a odstranění řádku v ovládacím prvku datagridview model Windows Forms](prevent-row-addition-and-deletion-datagridview.md)a [Postupy: vytvoření sloupců jen pro čtení v ovládacím prvku model Windows Forms DataGridView](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Ověřte vstup uživatele o chybách souvisejících s databází. Další informace naleznete v tématu [Návod: zpracování chyb, ke kterým došlo při zadávání dat v ovládacím prvku DataGridView model Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Přizpůsobení vzhledu buněk Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku model Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [Postup: nastavení výchozích stylů buňky pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
