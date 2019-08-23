---
title: Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918452"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView>sloupce mají tři režimy řazení. Režim řazení pro každý sloupec je zadán prostřednictvím <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnosti sloupce, který lze nastavit na jednu z následujících <xref:System.Windows.Forms.DataGridViewColumnSortMode> hodnot výčtu.  
  
|`DataGridViewColumnSortMode`osa|Popis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Výchozí pro sloupce textového pole Pokud se pro výběr nepoužívají záhlaví sloupců, kliknutím na záhlaví sloupce se automaticky <xref:System.Windows.Forms.DataGridView> seřadí sloupec podle tohoto sloupce a zobrazí se piktogram označující pořadí řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Výchozí pro sloupce bez textového pole Tento sloupec můžete seřadit programově; není však určena pro řazení, takže není vyhrazen prostor pro piktogram řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Tento sloupec můžete seřadit programově a místo pro piktogram řazení je vyhrazeno.|  
  
 Můžete chtít změnit režim řazení pro sloupec, který je ve výchozím nastavení <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> , pokud obsahuje hodnoty, které lze smysluplně seřadit. Například pokud máte sloupec databáze obsahující čísla, která představuje stavy položek, můžete zobrazit tato čísla jako odpovídající ikony navázáním sloupce obrázku na sloupec databáze. Pak můžete změnit hodnoty číselné buňky na hodnoty zobrazení obrázku v obslužné rutině <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> události. V takovém případě nastavením <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> vlastnosti umožníte uživatelům řazení sloupce. Automatické řazení umožní uživatelům seskupovat položky, které mají stejný stav, i když stavy odpovídající číslům nemají přirozené pořadí. Sloupce zaškrtávacích políček představují další příklad, ve kterém je automatické řazení užitečné pro seskupování položek ve stejném stavu.  
  
 Můžete <xref:System.Windows.Forms.DataGridView> programově řadit podle hodnot v jakémkoli sloupci nebo ve více sloupcích bez ohledu na <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavení. Programové řazení je užitečné, pokud chcete poskytnout vlastní uživatelské rozhraní (UI) pro řazení nebo pokud chcete implementovat vlastní řazení. Poskytování vlastního uživatelského rozhraní pro řazení je užitečné, například když nastavíte <xref:System.Windows.Forms.DataGridView> režim výběru tak, aby povoloval výběr záhlaví sloupce. V takovém případě, i když záhlaví sloupců nelze použít pro řazení, stále chcete, aby záhlaví zobrazovala příslušný piktogram pro řazení, takže byste <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost nastavili na. <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>  
  
 Sloupce nastavené na programový režim řazení nezobrazují automaticky piktogram řazení. Pro tyto sloupce je nutné zobrazit glyf sami nastavením <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> vlastnosti. To je nezbytné, pokud chcete mít flexibilitu při vlastním řazení. Například Pokud seřadíte <xref:System.Windows.Forms.DataGridView> podle více sloupců, můžete chtít zobrazit několik glyfů řazení nebo žádné piktogramy řazení.  
  
 I když můžete programově řadit <xref:System.Windows.Forms.DataGridView> podle libovolného sloupce, některé sloupce, například sloupce tlačítek, nemusí obsahovat hodnoty, které by mohly být smysluplně seřazené. U těchto sloupců <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> nastavení vlastnosti označuje, že nikdy nebude použito pro řazení, takže není nutné rezervovat místo v hlavičce pro piktogram řazení.  
  
 Při řazení <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> <xref:System.Windows.Forms.DataGridView.SortOrder%2A> je možné určit sloupec řazení i pořadí řazení, a to tak, že zkontrolujete hodnoty vlastností a. <xref:System.Windows.Forms.DataGridView> Tyto hodnoty nejsou smysluplné po vlastní operaci řazení. Další informace o vlastním řazení najdete v části vlastní řazení dále v tomto tématu.  
  
 Když je seřazen ovládací prvek obsahující jak vázané, tak nevázané sloupce, hodnoty v nevázaných sloupcích nelze automaticky spravovat. <xref:System.Windows.Forms.DataGridView> Chcete-li zachovat tyto hodnoty, je nutné implementovat virtuální režim nastavením <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnosti na `true` a zpracováním <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událostí <xref:System.Windows.Forms.DataGridView.CellValuePushed> a. Další informace najdete v tématu [jak: Implementace virtuálního režimu v ovládacím prvku](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms. Řazení podle nevázaných sloupců v vázaného režimu není podporováno.  
  
## <a name="programmatic-sorting"></a>Programové řazení  
 Můžete <xref:System.Windows.Forms.DataGridView> programově setřídit voláním jeho <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` Přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metodypřijímá<xref:System.Windows.Forms.DataGridViewColumn> a jako parametry vytvoří hodnotu výčtu.<xref:System.ComponentModel.ListSortDirection> Toto přetížení je užitečné při řazení podle sloupců s hodnotami, které mohou být smysluplně seřazeny, ale které nechcete konfigurovat pro automatické řazení. Při volání tohoto přetížení <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> a předání sloupce s <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>hodnotou vlastnosti, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> jsou vlastnosti a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> nastaveny automaticky a příslušný piktogram řazení se zobrazí v záhlaví sloupce.  
  
> [!NOTE]
> Když je <xref:System.Windows.Forms.DataGridView.DataSource%2A> `Sort(DataGridViewColumn,ListSortDirection)` ovládací prvek svázán s externím zdrojem dat nastavením vlastnosti, přetížení metody nefunguje pro nevázané sloupce. <xref:System.Windows.Forms.DataGridView> Kromě toho, pokud <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je `true`vlastnost, můžete volat tuto přetížení pouze pro vázané sloupce. Pokud chcete zjistit, jestli je sloupec vázaný na data, zkontrolujte <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> hodnotu vlastnosti. Řazení nevázaných sloupců ve vázaném režimu není podporováno.  
  
## <a name="custom-sorting"></a>Vlastní řazení  
 Můžete přizpůsobit <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.SortCompare> pomocí přetížení metody<xref:System.Windows.Forms.DataGridView.Sort%2A> nebo zpracováním události. `Sort(IComparer)`  
  
 Přetížení metody přebírá instanci třídy, která <xref:System.Collections.IComparer> implementuje rozhraní jako parametr. `Sort(IComparer)` Toto přetížení je užitečné, pokud chcete poskytnout vlastní řazení; Například pokud hodnoty ve sloupci nemají přirozené pořadí řazení, nebo když je přirozené pořadí řazení nevhodné. V tomto případě nemůžete použít automatické řazení, ale pokud chcete, aby se uživatelé mohli seřadit, klikněte na záhlaví sloupců. Toto přetížení můžete zavolat v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> , pokud nepoužijete záhlaví sloupců pro výběr.  
  
> [!NOTE]
> Přetížení metody funguje pouze v případě, <xref:System.Windows.Forms.DataGridView> že ovládací prvek není svázán s <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> externím zdrojem dat a hodnota vlastnosti je `false`. `Sort(IComparer)` Chcete-li přizpůsobit řazení sloupců vázaných na externí zdroj dat, je nutné použít operace řazení poskytované zdrojem dat. Ve virtuálním režimu musíte zadat vlastní operace řazení pro nevázané sloupce.  
  
 Chcete-li `Sort(IComparer)` použít přetížení metody, je nutné vytvořit vlastní třídu, která <xref:System.Collections.IComparer> implementuje rozhraní. Toto rozhraní vyžaduje, aby vaše třída implementovala <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> metodu, na <xref:System.Windows.Forms.DataGridView> kterou předává <xref:System.Windows.Forms.DataGridViewRow> objekty jako vstup při `Sort(IComparer)` volání metody přetížení. Díky tomu můžete vypočítat správné řazení řádků na základě hodnot v jakémkoli sloupci.  
  
 Přetížení metody nenastavuje <xref:System.Windows.Forms.DataGridView.SortOrder%2A> vlastnosti a, takže je nutné vždy nastavit vlastnosttak,abyzobrazovalapiktogramřazení.<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> `Sort(IComparer)`  
  
 Jako alternativu k `Sort(IComparer)` přetížení metody lze poskytnout vlastní řazení implementací obslužné rutiny <xref:System.Windows.Forms.DataGridView.SortCompare> pro událost. K této události dojde, když uživatel klikne na záhlaví sloupců nakonfigurované pro automatické řazení nebo při `Sort(DataGridViewColumn,ListSortDirection)` volání přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. K události dochází pro každou dvojici řádků v ovládacím prvku, což vám umožní vypočítat správné pořadí.  
  
> [!NOTE]
> K události nedojde, <xref:System.Windows.Forms.DataGridView.DataSource%2A> Pokud je nastavena vlastnost nebo pokud <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je `true`hodnota vlastnosti. <xref:System.Windows.Forms.DataGridView.SortCompare>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku DataGridView model Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Postupy: Přizpůsobení řazení v ovládacím prvku DataGridView model Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
