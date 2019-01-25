---
title: Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b2b73d36230d12f4e1075dde201e941cbe9d228d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615046"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> sloupce mají tři režimy řazení. Režim řazení pro každý sloupec se specifikuje prostřednictvím <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost sloupec, který může být nastavena na jednu z následujících <xref:System.Windows.Forms.DataGridViewColumnSortMode> hodnot výčtu.  
  
|`DataGridViewColumnSortMode` Hodnota|Popis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Výchozí nastavení pro textové pole sloupce. Pokud nepoužíváte záhlaví sloupců jsou pro výběr, automaticky kliknutím na záhlaví sloupce seřadí <xref:System.Windows.Forms.DataGridView> podle tohoto sloupce a zobrazí piktogram určující pořadí řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Výchozí hodnoty pro sloupce bez – textové pole. Tento sloupec lze seřadit prostřednictvím kódu programu; ale není určena pro řazení, tak žádné místo je vyhrazený pro řazení glyfů.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Tento sloupec lze seřadit prostřednictvím kódu programu a je vyhrazen prostor pro řazení glyfů.|  
  
 Můžete chtít změnit režim řazení pro sloupce, který se použije výchozí <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> pokud obsahuje hodnoty, které lze provést smysluplně řazení. Například pokud máte databáze sloupec obsahující čísla, která představují stavy položky, můžete zobrazit tato čísla jako odpovídajících ikon navázáním sloupce obrázku na sloupce databáze. Můžete změnit hodnoty číselné buněk do image zobrazovaných hodnot v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. V takovém případě nastavení <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> vám umožní vašim uživatelům seřadí hodnoty ve sloupci. Automatické řazení vám umožní vašim uživatelům seskupení položek, které mají stejného stavu i v případě stavů odpovídající čísla nemají přirozené pořadí. Zaškrtávací políčko sloupce jsou další příklad, kde automatické řazení je užitečné pro seskupení položek v nezměněném stavu.  
  
 Můžete řadit <xref:System.Windows.Forms.DataGridView> prostřednictvím kódu programu pomocí hodnot, na jakémkoli sloupci nebo ve více sloupcích, bez ohledu <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavení. Programové řazení je užitečné, pokud chcete poskytnout vlastní uživatelské rozhraní (UI) pro řazení nebo pokud chcete implementovat vlastní řazení. Poskytující řazení uživatelské rozhraní je užitečné, například při nastavení <xref:System.Windows.Forms.DataGridView> režim výběru umožníte výběr záhlaví sloupce. V takovém případě i když nelze zadat záhlaví sloupců pro řazení, stále chcete hlavičky k zobrazení odpovídající řazení šifra, takže byste měli nastavit <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Nastavit na režim programový řazení sloupce řazení piktogram automaticky nezobrazují. Pro tyto sloupce, je třeba zobrazit glyf sami tak, že nastavíte <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> vlastnost. To je nezbytné, pokud požadujete flexibilitu ve vlastní řazení. Například při řazení <xref:System.Windows.Forms.DataGridView> více sloupců, můžete chtít zobrazit více glyfy řazení nebo glyfů žádné řazení.  
  
 I když můžete programově řadit <xref:System.Windows.Forms.DataGridView> podle libovolného sloupce, nemusí některé sloupce, jako je například tlačítko sloupce obsahují hodnoty, které lze provést řazení smysluplně. Pro tyto sloupce <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavení vlastnosti <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> označuje, že se nebudou nikdy použity k řazení, takže není nutné rezervovat místa v záhlaví pro řazení glyfů.  
  
 Když <xref:System.Windows.Forms.DataGridView> je seřazený, můžete určit řazení sloupců a pořadí řazení kontrolou hodnoty <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti. Tyto hodnoty nejsou smysluplné po vlastní operace řazení. Další informace o vlastní řazení naleznete v části vlastní řazení dále v tomto tématu.  
  
 Když <xref:System.Windows.Forms.DataGridView> ovládací prvek obsahující provázaná a nevázaného sloupce má řazení proběhnout, hodnoty v nevázaných sloupců nelze automaticky udržuje. Pokud chcete zachovat tyto hodnoty, je nutné implementovat virtuální režim nastavením <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a zpracování <xref:System.Windows.Forms.DataGridView.CellValueNeeded> a <xref:System.Windows.Forms.DataGridView.CellValuePushed> události. Další informace najdete v tématu [jak: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Řazení podle nevázaných sloupců v vázaný režimu není podporováno.  
  
## <a name="programmatic-sorting"></a>Řazení prostřednictvím kódu programu  
 Můžete řadit <xref:System.Windows.Forms.DataGridView> programově zavoláním jeho <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> přijímá metodu <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.ComponentModel.ListSortDirection> hodnota výčtu jako parametry. Toto přetížení je užitečná při řazení podle sloupce s hodnotami, které lze provést smysluplně řazení, ale které nechcete nakonfigurovat pro automatické řazení. Při volání tohoto přetížení a předejte mu sloupec <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> hodnotou vlastnosti <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti nastaví automaticky a odpovídající řazení šifra se zobrazí v záhlaví sloupce.  
  
> [!NOTE]
>  Když <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán k externímu zdroji dat tím, že nastavíte <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost, `Sort(DataGridViewColumn,ListSortDirection)` přetížení metody nefunguje pro nevázaných sloupců. Kromě toho, kdy <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true`, toto přetížení lze volat pouze u sloupců vázaných. Chcete-li zjistit, zda sloupec je vázané na data, zkontrolujte <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> hodnotu vlastnosti. Řazení nevázaných sloupců v vázaný režimu není podporováno.  
  
## <a name="custom-sorting"></a>Vlastní řazení  
 Můžete přizpůsobit <xref:System.Windows.Forms.DataGridView> pomocí `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda nebo zpracování <xref:System.Windows.Forms.DataGridView.SortCompare> událostí.  
  
 `Sort(IComparer)` Metody přetížení přijímající instanci třídy, která implementuje <xref:System.Collections.IComparer> rozhraní jako parametr. Toto přetížení je užitečné, pokud chcete zadat vlastní řazení; například když hodnoty ve sloupci nemají přirozené pořadí řazení nebo když fyzická pořadí řazení je nevhodná. V takovém případě nemůžete použít automatické řazení, ale stále můžete uživatelům seřadit klepnutím na záhlaví sloupců. Toto přetížení můžete volat obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> událost, pokud nepoužijete záhlaví sloupců pro výběr.  
  
> [!NOTE]
>  `Sort(IComparer)` Přetížení metody funguje pouze tehdy, když <xref:System.Windows.Forms.DataGridView> ovládací prvek není vázán k externímu zdroji dat a <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> hodnota vlastnosti je `false`. Přizpůsobení řazení pro sloupce vázán k externímu zdroji dat, je nutné použít operace řazení podle zdroje dat k dispozici. Ve virtuálním režimu je nutné zadat vlastní operace řazení pro nevázaných sloupců.  
  
 Použít `Sort(IComparer)` přetížení metody, je třeba vytvořit vlastní třídu, která implementuje <xref:System.Collections.IComparer> rozhraní. Toto rozhraní vyžaduje třídu pro implementaci <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> metodu, která <xref:System.Windows.Forms.DataGridView> předá <xref:System.Windows.Forms.DataGridViewRow> objekty jako vstup při `Sort(IComparer)` volat přetížení metody. Díky tomu můžete vypočítat správný řádek pořadí na základě hodnot na jakémkoli sloupci.  
  
 `Sort(IComparer)` Přetížení metody nenastaví <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti, tak musí vždycky nastavená <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> vlastnost pro zobrazení řazení glyfů.  
  
 Jako alternativu k `Sort(IComparer)` přetížení metody, můžete zadat vlastní řazení pomocí implementace obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.SortCompare> událostí. K této události dojde, když uživatelé kliknou na záhlaví sloupce, které jsou nakonfigurované pro automatické řazení nebo při volání `Sort(DataGridViewColumn,ListSortDirection)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Pro každý pár řádků v ovládacím prvku, můžete k výpočtu jejich správné pořadí dojde k události.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Události nedochází při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo pokud <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> hodnota vlastnosti je `true`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
