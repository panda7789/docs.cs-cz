---
title: Virtuální režim v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f2ab0cc789b026a139e1421b72e9215bf52c6147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672016"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Virtuální režim v ovládacím prvku Windows Forms DataGridView
Virtuální režim, můžete spravovat interakce mezi <xref:System.Windows.Forms.DataGridView> ovládacího prvku a vlastní datové mezipaměti. Implementace virtuálního režimu, nastavte <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a zpracovat jeden nebo více událostí, které jsou popsané v tomto tématu. Obvykle budete zpracovávat alespoň `CellValueNeeded` událost, která umožňuje vyhledat ovládací prvek hodnoty v datové mezipaměti.  
  
## <a name="bound-mode-and-virtual-mode"></a>Vazby a virtuálního režimu  
 Virtuální režim je nezbytné pouze v případě, že budete muset doplněk nebo nahradit vázané režimu. Ve vázané režimu, můžete nastavit <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastností a ovládací prvek automaticky načte data ze zadaného zdroje a odešle změnu zpět do něj. Můžete řídit, které svázané sloupce se zobrazí a zdroj dat, samotný obvykle zpracovává operace, jako je řazení.  
  
## <a name="supplementing-bound-mode"></a>Doplňující vázané režimu  
 Vázané režimu můžete doplnit zobrazení nevázaných sloupců spolu s svázané sloupce. To se někdy označuje jako "ve smíšeném režimu" a je vhodný pro zobrazování záležitostmi, jako je vypočítané hodnoty nebo uživatelského rozhraní (UI) ovládací prvky.  
  
 Vzhledem k tomu nevázaného sloupce mimo zdroj dat, jsou ignorovány ve zdroji dat operace řazení. Proto když povolíte řazení ve smíšeném režimu, musíte spravovat nevázaných dat v místní mezipaměti a implementace virtuálního režimu chcete, aby <xref:System.Windows.Forms.DataGridView> ovládacího prvku s ní pracovat.  
  
 Další informace o použití virtuální režimu pro zachování hodnot v nevázaných sloupců, podívejte se na příklady v <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> třídy referenční témata.  
  
## <a name="replacing-bound-mode"></a>Nahrazení vázané režimu  
 Pokud vázané režim nesplňuje vašim požadavkům na výkon, můžete spravovat všechna data na vlastní mezipaměti prostřednictvím obslužné rutiny událostí virtuálním režimu. Například můžete použít virtuální režim implementovat just-in-time data načítání mechanismus, který načte pouze tolik dat z databáze síti je nezbytné k zajištění optimálního výkonu. Tento scénář je zvlášť užitečné při práci s velkými objemy dat přes pomalé připojení k síti nebo s klientskými počítači, které mají omezenou velikost paměti RAM nebo prostor úložiště.  
  
 Další informace o používání virtuálního režimu v případě just-in-time najdete v tématu [implementace virtuálního režimu s načítáním dat k za běhu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Virtuální režim události  
 Pokud vaše data jsou jen pro čtení, `CellValueNeeded` události může být pouze události, je potřeba zpracovat. Další události virtuálního režimu umožňují povolit konkrétní funkce, jako jsou uživatelské úpravy, přidávání řádků a odstranění a transakce na úrovni řádků.  
  
 Některé standardní <xref:System.Windows.Forms.DataGridView> události (například události, ke které dochází, když uživatelé přidat nebo odstranit řádky nebo když buňky hodnoty jsou upravovat, analyzovat, ověřit nebo ve formátu) jsou užitečné ve virtuálním režimu, také. Můžete také zpracovávat události, které vám umožňují udržovat hodnoty obvykle nejsou uložené ve zdroji vazby dat, například text popisu buňky, buňky a text řádku chyby, buňky a dat místní nabídku řádku a data výšku řádku.  
  
 Další informace o implementace virtuálního režimu pro správu dat pro čtení a zápisu s rozsahem potvrzení změn na úrovni řádků, naleznete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Příklad, který implementuje virtuálního režimu s rozsahem potvrzení na úrovni buněk, najdete v článku <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost referenční téma.  
  
 Pouze dojde k následujícím událostem při <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je nastavena na `true`.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|K načtení hodnoty buňky z mezipaměti dat pro zobrazení používá ovládací prvek. Pouze u buněk v nevázaných sloupců dojde k této události.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Potvrdit uživatelský vstup pro buňku mezipaměť dat používané ovládací prvek. Pouze u buněk v nevázaných sloupců dojde k této události.<br /><br /> Volání <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metoda při změně hodnotu uloženou v mezipaměti mimo <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužná rutina události, ujistěte se, že aktuální hodnota se zobrazí v ovládacím prvku a aplikovat všechny režimy automatické velikosti aktuálně používána.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Používá ovládací prvek k označení potřebu nový řádek v datové mezipaměti.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Ovládací prvek používá k určení, zda řádek obsahuje všechny nepotvrzené změny.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Ovládací prvek se používá k označení, že řádek by měl vrátit k její hodnoty uložené v mezipaměti.|  
  
 Tyto události jsou užitečné ve virtuálním režimu, ale je možné bez ohledu na to <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavení vlastnosti.  
  
|Události|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Používá ovládací prvek k označení při řádky budou odstraněny nebo přidání, takže můžete aktualizovat datové mezipaměti odpovídajícím způsobem.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Pomocí ovládacího prvku, aby formát hodnoty buněk pro zobrazení a analýza a ověření vstupu uživatele.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Používá k načtení text popisu buňky v ovládacím prvku při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true`.<br /><br /> Popisy tlačítek buňky se zobrazují pouze tehdy, když <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> hodnota vlastnosti je `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Použit v ovládacím prvku pro načtení buňku nebo řádek text chyby při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true`.<br /><br /> Volání <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> metoda nebo <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> metoda při změně buňku nebo řádek text chyby k zajištění, že aktuální hodnota se zobrazí v ovládacím prvku.<br /><br /> Piktogramy řádků a buňky se zobrazují při <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> a <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> hodnoty vlastností jsou `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Použit v ovládacím prvku pro načtení buňku nebo řádek <xref:System.Windows.Forms.ContextMenuStrip> při ovládací prvek <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Používá k načtení nebo uložení informace výšku řádků v datové mezipaměti ovládacího prvku. Volání <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> metoda při změně výška informace uložené v mezipaměti řádek mimo <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> obslužná rutina události, chcete-li zajistit, aby používal aktuální hodnotu v zobrazení ovládacího prvku.|  
  
## <a name="best-practices-in-virtual-mode"></a>Osvědčené postupy ve virtuálním režimu  
 Pokud chcete-li efektivně pracovat s velkými objemy dat jsou implementace virtuálního režimu, bude také chcete zajistit, že pracujete efektivně <xref:System.Windows.Forms.DataGridView> samotného ovládacího prvku. Další informace o efektivní využití stylů buňky, automatické velikosti, výběr a řádků pro sdílení obsahu najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
- [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
