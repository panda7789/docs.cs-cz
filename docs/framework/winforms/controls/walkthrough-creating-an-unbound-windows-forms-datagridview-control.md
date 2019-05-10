---
title: 'Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView'
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
ms.openlocfilehash: ba821b461434cb7a5247d2962a161a1c171bbd14
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651462"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView
Můžete často zobrazit tabulková data, která nepochází z databáze. Můžete například zobrazit obsah dvourozměrné pole řetězců. <xref:System.Windows.Forms.DataGridView> Třída poskytuje snadný a dobře přizpůsobitelných způsob zobrazení dat bez vazby ke zdroji dat. Tento návod ukazuje, jak naplnit <xref:System.Windows.Forms.DataGridView> řídit a spravovat přidávání a odstraňování řádků v režim "bez vazby". Ve výchozím nastavení může uživatel přidat nové řádky. Chcete-li zabránit přidání řádku, nastavte <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost `false`.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Vytvoření ovládacího prvku DataGridView formuláře Windows nevázaného](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Chcete-li použít nevázaného ovládacího prvku DataGridView  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje následující deklarace proměnných a `Main` metoda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. Implementace `SetupLayout` metoda v definici třídy formuláře k nastavení rozložení formuláře.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. Vytvoření `SetupDataGridView` metoda nastavit <xref:System.Windows.Forms.DataGridView> sloupců a vlastnosti.  
  
     Tato metoda nejprve přidá <xref:System.Windows.Forms.DataGridView> ovládací prvek do formuláře <xref:System.Windows.Forms.Control.Controls%2A> kolekce. Počet sloupců, který se má zobrazit v dalším kroku se nastavuje pomocí <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> vlastnost. Výchozí styl záhlaví sloupců je nastavena tak, že nastavíte <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, a <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> vrácených <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> vlastnost.  
  
     Jsou nastaveny vlastnosti rozložení a vzhled a pak se přiřadí názvy sloupců. Při ukončení této metody <xref:System.Windows.Forms.DataGridView> ovládací prvek je připraven, který se má naplnit.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. Vytvoření `PopulateDataGridView` metoda pro přidání řádků do <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Každý řádek představuje určité skladby a přidružené informace.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. Pomocí pomocné metody na místě můžete připojit obslužných rutin událostí.  
  
     Bude zpracovávat **přidat** a **odstranit** tlačítka <xref:System.Windows.Forms.Control.Click> události, formuláře <xref:System.Windows.Forms.Form.Load> události a <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.  
  
     Když **přidat** tlačítka <xref:System.Windows.Forms.Control.Click> událost se vyvolá, nový, prázdný řádek přidán do <xref:System.Windows.Forms.DataGridView>.  
  
     Když **odstranit** tlačítka <xref:System.Windows.Forms.Control.Click> událost se vyvolá, se odstraní vybraný řádek, pokud je řádek pro nové záznamy, který uživateli umožňuje přidání nových řádků. Tento řádek je vždy poslední řádek v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Při formuláře <xref:System.Windows.Forms.Form.Load> událost se vyvolá, `SetupLayout`, `SetupDataGridView`, a `PopulateDataGridView` pomocné metody jsou volány.  
  
     Když <xref:System.Windows.Forms.DataGridView.CellFormatting> událost se vyvolá, každá buňka `Date` sloupec je formátován jako dlouhého data, pokud hodnota buňky nelze analyzovat.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
- Stisknutím klávesy F5 spusťte aplikaci.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí skladeb uvedené v `PopulateDataGridView`. Můžete přidat nové řádky s **přidat řádek** tlačítko a můžete odstranit vybrané řádky s **odstranit řádek** tlačítko. Nepřipojeného <xref:System.Windows.Forms.DataGridView> ovládací prvek je úložiště dat a jeho data, jako je nezávislá jakéhokoli externího zdroje <xref:System.Data.DataSet> nebo pole.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o <xref:System.Windows.Forms.DataGridView> možnosti ovládacího prvku. Můžete přizpůsobit vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku v několika ohledech:  
  
- Změna stylů ohraničení a záhlaví. Další informace najdete v tématu [jak: Změna ohraničení a styly mřížky v Windows Forms DataGridView](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Povolit nebo zakázat vstup uživatele <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Další informace najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md), a [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView – ovládací prvek](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Zkontrolujte chyby související s databáze uživatelský vstup. Další informace najdete v tématu [názorný postup: Zpracování chyb vzniklých při zadávání dat v Windows Forms DataGridView – ovládací prvek](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Zpracování velmi rozsáhlým datovým sadám pomocí virtuální režim. Další informace najdete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Přizpůsobení vzhledu buněk. Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [jak: Nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření ovládacího prvku nevázaného Windows Forms DataGridView](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
