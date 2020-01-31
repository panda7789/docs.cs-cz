---
title: Režimy řazení sloupců v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d1e2f582c9759332e0ed963cb7f88ee052616c45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744190"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> sloupce mají tři režimy řazení. Režim řazení pro každý sloupec je zadán prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> sloupce, který lze nastavit na jednu z následujících <xref:System.Windows.Forms.DataGridViewColumnSortMode> hodnot výčtu.  
  
|hodnota `DataGridViewColumnSortMode`|Popis|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Výchozí pro sloupce textového pole Pokud se pro výběr nepoužívají záhlaví sloupců, kliknutím na záhlaví sloupce se automaticky seřadí <xref:System.Windows.Forms.DataGridView> podle tohoto sloupce a zobrazí se piktogram označující pořadí řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Výchozí pro sloupce bez textového pole Tento sloupec můžete seřadit programově; není však určena pro řazení, takže není vyhrazen prostor pro piktogram řazení.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Tento sloupec můžete seřadit programově a místo pro piktogram řazení je vyhrazeno.|  
  
 Můžete chtít změnit režim řazení pro sloupec, který je ve výchozím nastavení <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>, pokud obsahuje hodnoty, které mohou být seřazeny smysluplně. Například pokud máte sloupec databáze obsahující čísla, která představuje stavy položek, můžete zobrazit tato čísla jako odpovídající ikony navázáním sloupce obrázku na sloupec databáze. Pak můžete změnit hodnoty číselné buňky na obrázek hodnoty zobrazení v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. V takovém případě nastavením vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> na <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> umožníte uživatelům řazení sloupce. Automatické řazení umožní uživatelům seskupovat položky, které mají stejný stav, i když stavy odpovídající číslům nemají přirozené pořadí. Sloupce zaškrtávacích políček představují další příklad, ve kterém je automatické řazení užitečné pro seskupování položek ve stejném stavu.  
  
 <xref:System.Windows.Forms.DataGridView> můžete seřadit programově podle hodnot v jakémkoli sloupci nebo ve více sloupcích bez ohledu na nastavení <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>. Programové řazení je užitečné, pokud chcete poskytnout vlastní uživatelské rozhraní (UI) pro řazení nebo pokud chcete implementovat vlastní řazení. Poskytování vlastního uživatelského rozhraní pro řazení je užitečné, například když nastavíte režim výběru <xref:System.Windows.Forms.DataGridView> tak, aby se povolil výběr záhlaví sloupce. V takovém případě, i když záhlaví sloupců nelze použít pro řazení, stále chcete, aby záhlaví zobrazovala příslušné piktogramy řazení, takže byste vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavili na hodnotu <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Sloupce nastavené na programový režim řazení nezobrazují automaticky piktogram řazení. Pro tyto sloupce je nutné zobrazit glyf sami nastavením vlastnosti <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>. To je nezbytné, pokud chcete mít flexibilitu při vlastním řazení. Například Pokud seřadíte <xref:System.Windows.Forms.DataGridView> podle více sloupců, může být vhodné zobrazit více glyfů řazení nebo žádný piktogram řazení.  
  
 I když můžete programově seřadit <xref:System.Windows.Forms.DataGridView> podle libovolného sloupce, některé sloupce, například sloupce tlačítek, nemusí obsahovat hodnoty, které by mohly být smysluplně seřazené. Pro tyto sloupce <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> nastavení vlastnosti <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> označuje, že nikdy nebude použito pro řazení, takže není nutné rezervovat místo v hlavičce pro piktogram řazení.  
  
 Při řazení <xref:System.Windows.Forms.DataGridView> můžete určit sloupec řazení i pořadí řazení, a to tak, že zkontrolujete hodnoty vlastností <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. Tyto hodnoty nejsou smysluplné po vlastní operaci řazení. Další informace o vlastním řazení najdete v části vlastní řazení dále v tomto tématu.  
  
 Když je seřazený <xref:System.Windows.Forms.DataGridView> ovládací prvek obsahující jak vázané, tak nevázané sloupce, hodnoty v nevázaných sloupcích nelze automaticky spravovat. Chcete-li zachovat tyto hodnoty, je nutné implementovat virtuální režim nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` a zpracováním <xref:System.Windows.Forms.DataGridView.CellValueNeeded> a <xref:System.Windows.Forms.DataGridView.CellValuePushed>ch událostí. Další informace naleznete v tématu [Postupy: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Řazení podle nevázaných sloupců v vázaného režimu není podporováno.  
  
## <a name="programmatic-sorting"></a>Programové řazení  
 <xref:System.Windows.Forms.DataGridView> lze seřadit programově voláním metody <xref:System.Windows.Forms.DataGridView.Sort%2A>.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A> přebírá <xref:System.Windows.Forms.DataGridViewColumn> a hodnotu výčtu <xref:System.ComponentModel.ListSortDirection> jako parametry. Toto přetížení je užitečné při řazení podle sloupců s hodnotami, které mohou být smysluplně seřazeny, ale které nechcete konfigurovat pro automatické řazení. Při volání tohoto přetížení a předání sloupce s hodnotou <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>jsou vlastnosti <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A> nastaveny automaticky a příslušný piktogram pro řazení se zobrazí v záhlaví sloupce.  
  
> [!NOTE]
> Když je ovládací prvek <xref:System.Windows.Forms.DataGridView> vázaný na externí zdroj dat nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A>, přetížení metody `Sort(DataGridViewColumn,ListSortDirection)` nefunguje pro nevázané sloupce. Kromě toho, pokud je vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`, lze toto přetížení volat pouze pro vázané sloupce. Pokud chcete zjistit, jestli je sloupec vázaný na data, zkontrolujte hodnotu vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>. Řazení nevázaných sloupců ve vázaném režimu není podporováno.  
  
## <a name="custom-sorting"></a>Vlastní řazení  
 Můžete přizpůsobit <xref:System.Windows.Forms.DataGridView> pomocí `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metody nebo zpracováním <xref:System.Windows.Forms.DataGridView.SortCompare> události.  
  
 Přetížení metody `Sort(IComparer)` přebírá instanci třídy, která implementuje rozhraní <xref:System.Collections.IComparer> jako parametr. Toto přetížení je užitečné, pokud chcete poskytnout vlastní řazení; Například pokud hodnoty ve sloupci nemají přirozené pořadí řazení, nebo když je přirozené pořadí řazení nevhodné. V tomto případě nemůžete použít automatické řazení, ale pokud chcete, aby se uživatelé mohli seřadit, klikněte na záhlaví sloupců. Toto přetížení můžete zavolat v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>, pokud nepoužijete záhlaví sloupců pro výběr.  
  
> [!NOTE]
> Přetížení metody `Sort(IComparer)` funguje pouze v případě, že ovládací prvek <xref:System.Windows.Forms.DataGridView> není svázán s externím zdrojem dat a hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je `false`. Chcete-li přizpůsobit řazení sloupců vázaných na externí zdroj dat, je nutné použít operace řazení poskytované zdrojem dat. Ve virtuálním režimu musíte zadat vlastní operace řazení pro nevázané sloupce.  
  
 Chcete-li použít přetížení metody `Sort(IComparer)`, je nutné vytvořit vlastní třídu, která implementuje rozhraní <xref:System.Collections.IComparer>. Toto rozhraní vyžaduje, aby vaše třída implementovala metodu <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>, na kterou <xref:System.Windows.Forms.DataGridView> předává <xref:System.Windows.Forms.DataGridViewRow> objekty jako vstup, když je volána přetížená metoda `Sort(IComparer)`. Díky tomu můžete vypočítat správné řazení řádků na základě hodnot v jakémkoli sloupci.  
  
 Přetížení metody `Sort(IComparer)` nenastavuje vlastnosti <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> a <xref:System.Windows.Forms.DataGridView.SortOrder%2A>, takže je nutné vždy nastavit vlastnost <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>, aby zobrazila piktogram řazení.  
  
 Jako alternativu k přetížení metody `Sort(IComparer)` můžete poskytnout vlastní řazení implementací obslužné rutiny pro událost <xref:System.Windows.Forms.DataGridView.SortCompare>. K této události dojde, když uživatel klikne na záhlaví sloupců nakonfigurované pro automatické řazení nebo při volání `Sort(DataGridViewColumn,ListSortDirection)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A>. K události dochází pro každou dvojici řádků v ovládacím prvku, což vám umožní vypočítat správné pořadí.  
  
> [!NOTE]
> K události <xref:System.Windows.Forms.DataGridView.SortCompare> nedojde, je-li nastavena vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A> nebo je-li hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`a.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
