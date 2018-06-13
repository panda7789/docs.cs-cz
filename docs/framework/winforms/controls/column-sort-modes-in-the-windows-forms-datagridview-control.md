---
title: Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: 9ebcfc435fcc7d2b0dfbfe3004d958c73dd1347c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529685"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> sloupce mít tři režimy řazení. Režim řazení pro každý sloupec se specifikuje prostřednictvím <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost sloupce, který může být nastaven na jednu z následujících <xref:System.Windows.Forms.DataGridViewColumnSortMode> hodnot výčtu.  
  
|`DataGridViewColumnSortMode` Hodnota|Popis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Výchozí hodnoty pro textové pole sloupců. Pokud záhlaví sloupců se používají pro výběr, automaticky kliknutím na záhlaví sloupce seřadí <xref:System.Windows.Forms.DataGridView> podle tohoto sloupce a zobrazí glyf označující pořadí řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Výchozí hodnoty pro sloupce bez – textové pole. Tento sloupec lze seřadit prostřednictvím kódu programu; však není určen pro řazení, takže žádné místo je vyhrazený pro řazení glyfů.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Tento sloupec lze seřadit prostřednictvím kódu programu a prostor je vyhrazen pro řazení glyfů.|  
  
 Můžete chtít změnit režim řazení pro sloupec, který použije se výchozí hodnota <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> pokud obsahuje hodnoty, které lze provést řazení mohli vytvořit smysluplný. Například pokud máte databáze sloupec obsahující čísla, která představují stavy položek, můžete zobrazit tato čísla jako ikony odpovídající pomocí vytvoření vazby sloupce obrázku ke sloupci databáze. Můžete změnit hodnoty číselné buněk do bitové kopie zobrazovaných hodnot v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. V takovém případě nastavení <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> vám umožní uživatelům seřadí hodnoty ve sloupci. Automatické řazení vám umožní uživatelům skupiny položky, které mají stejného stavu, i když stavy odpovídající čísla, která nemají přirozené pořadí. Zaškrtněte políčko sloupce jsou další příklad, kdy automatické řazení je užitečné pro seskupení položek v takovém stavu.  
  
 Můžete řadit <xref:System.Windows.Forms.DataGridView> prostřednictvím kódu programu podle hodnot v žádný sloupec nebo ve více sloupců, bez ohledu <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavení. Programová řazení je užitečné, pokud chcete zadat vlastní uživatelské rozhraní (UI) pro řazení nebo pokud chcete implementovat vlastní řazení. Pokud řazení uživatelské rozhraní je užitečné, například pokud nastavíte <xref:System.Windows.Forms.DataGridView> režim výběru umožňující výběr záhlaví sloupců. V takovém případě i když na záhlaví sloupce nelze použít k řazení, stále chcete hlavičky zobrazíte příslušné řazení glyf, takže byste měli nastavit <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Sloupcích nastavených na režim programový řazení řazení glyf automaticky nezobrazují. Pro tyto sloupce je třeba zobrazit glyf sami nastavením <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> vlastnost. To je nezbytné, pokud chcete flexibilitu v vlastní řazení. Například pokud jste <xref:System.Windows.Forms.DataGridView> podle více sloupců, můžete chtít zobrazit více řazení glyfů nebo žádné řazení glyfů.  
  
 I když můžete programově řadit <xref:System.Windows.Forms.DataGridView> podle všechny sloupce, nemusí některé sloupce, např. tlačítka sloupců, obsahují hodnoty, které lze provést řazení mohli vytvořit smysluplný. Pro tyto sloupce <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost na hodnotu <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> označuje, že ho bude použít nikdy pro řazení, takže není nutné rezervovat místo v hlavičce pro řazení glyfů.  
  
 Když <xref:System.Windows.Forms.DataGridView> je seřadit, můžete určit sloupec pro řazení a pořadí řazení kontrolou hodnoty <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti. Tyto hodnoty nejsou smysluplný po operaci vlastní řazení. Další informace o vlastní řazení najdete v části vlastní řazení později v tomto tématu.  
  
 Když <xref:System.Windows.Forms.DataGridView> seřazená ovládací prvek obsahující vázaných a nevázaných sloupců, hodnoty v nevázaných sloupců nelze udržovat automaticky. Pokud chcete zachovat tyto hodnoty, je nutné implementovat virtuální režim nastavením <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a zpracování <xref:System.Windows.Forms.DataGridView.CellValueNeeded> a <xref:System.Windows.Forms.DataGridView.CellValuePushed> události. Další informace najdete v tématu [postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Řazení podle nevázaných sloupců v vázané režimu není podporována.  
  
## <a name="programmatic-sorting"></a>Programová řazení  
 Můžete řadit <xref:System.Windows.Forms.DataGridView> programově zavoláním jeho <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda trvá <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.ComponentModel.ListSortDirection> hodnota výčtu jako parametry. Toto přetížení je užitečné, když řazení podle sloupce s hodnotami, které lze provést srozumitelně řazení, ale které nechcete nakonfigurovat pro automatické řazení. Při volání toto přetížení a předat ve sloupci s <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> jsou automaticky nastavené vlastnosti a příslušné řazení glyfy se zobrazí v záhlaví sloupce.  
  
> [!NOTE]
>  Když <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán k externímu zdroji dat nastavením <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost, `Sort(DataGridViewColumn,ListSortDirection)` přetížení metody nefunguje pro nevázaných sloupců. Kromě toho, když <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`, toto přetížení můžete volat pouze pro sloupce vázané. Chcete-li zjistit, zda sloupec je vázané na data, zkontrolujte <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> hodnotu vlastnosti. Řazení nevázaných sloupců v vázané režimu není podporována.  
  
## <a name="custom-sorting"></a>Vlastní řazení  
 Můžete přizpůsobit <xref:System.Windows.Forms.DataGridView> pomocí `Sort(IComparer)` přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda nebo zpracování <xref:System.Windows.Forms.DataGridView.SortCompare> událostí.  
  
 `Sort(IComparer)` Přetížení metody trvá instance třídy, který implementuje <xref:System.Collections.IComparer> rozhraní jako parametr. Toto přetížení se hodí, pokud chcete zadat vlastní řazení; například když hodnoty ve sloupci nemají přirozené pořadí řazení nebo když přirozený pořadí řazení je nevhodný. V tomto případě nemůžete použít automatické řazení, ale stále můžete uživatelům můžete seřadit kliknutím na záhlaví sloupců. Toto přetížení můžete volat v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> událost, pokud nepoužíváte záhlaví sloupců pro výběr.  
  
> [!NOTE]
>  `Sort(IComparer)` Přetížení metody funguje pouze tehdy, když <xref:System.Windows.Forms.DataGridView> ovládací prvek není vázán k externímu zdroji dat a <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> hodnota vlastnosti je `false`. Chcete-li přizpůsobení třídění pro sloupce, které jsou vázány na externí zdroj dat, musíte použít operace řazení zadaný zdroj dat. Ve virtuálním režimu je nutné zadat vlastní řazení operací pro nevázaných sloupců.  
  
 Chcete-li použít `Sort(IComparer)` přetížení metody, musíte vytvořit vlastní třídu, která implementuje <xref:System.Collections.IComparer> rozhraní. Toto rozhraní vyžaduje vlastní třídy k implementaci <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> metoda, ke kterému <xref:System.Windows.Forms.DataGridView> předá <xref:System.Windows.Forms.DataGridViewRow> objekty jako vstup, kdy `Sort(IComparer)` se nazývá přetížení metody. S tím můžete vypočítat správný řádek řazení na základě hodnot v žádné sloupce.  
  
 `Sort(IComparer)` Přetížení metody nenastaví <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti, takže vždy musíte nastavit <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> vlastnost zobrazíte řazení glyfů.  
  
 Jako alternativu k `Sort(IComparer)` přetížení metody, můžete zadat vlastní řazení implementací obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.SortCompare> událostí. K této události dojde, když uživatelé kliknou na záhlaví sloupce, které jsou konfigurovány pro automatické řazení nebo při volání `Sort(DataGridViewColumn,ListSortDirection)` přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda. Pro každý pár řádků v ovládacím prvku umožňuje vypočítat jejich správné pořadí dojde k události.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Události nedojde při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo když <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> hodnota vlastnosti je `true`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>  
 [Řazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 [Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
