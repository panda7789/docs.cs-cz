---
title: Osvědčené postupy pro škálování ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744133"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Doporučené postupy pro změnu velikosti v ovládacím prvku Windows Forms DataGridView

<xref:System.Windows.Forms.DataGridView> ovládací prvek je navržen tak, aby poskytoval maximální škálovatelnost. Pokud potřebujete zobrazit velké objemy dat, měli byste postupovat podle pokynů popsaných v tomto tématu, abyste se vyhnuli využívání velkých objemů paměti nebo snížení rychlosti odezvy uživatelského rozhraní (UI). Toto téma popisuje následující problémy:

- Efektivní použití stylů buněk

- Efektivní používání místních nabídek

- Efektivní použití automatické změny velikosti

- Efektivní používání kolekcí vybraných buněk, řádků a sloupců

- Použití sdílených řádků

- Zabránění nesdílení řádků

Pokud máte zvláštní požadavky na výkon, můžete implementovat virtuální režim a poskytnout své vlastní operace správy dat. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku DataGridView model Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Efektivní použití stylů buněk

Jednotlivé buňky, řádky a sloupce mohou mít vlastní informace o stylu. Informace o stylu jsou uloženy v <xref:System.Windows.Forms.DataGridViewCellStyle> objekty. Vytváření objektů stylu buňky pro mnoho jednotlivých <xref:System.Windows.Forms.DataGridView> prvků může být neefektivní, zejména při práci s velkým objemem dat. Abyste se vyhnuli dopadu na výkon, postupujte podle následujících pokynů:

- Vyhněte se nastavení vlastností stylu buňky pro jednotlivé objekty <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewRow>. To zahrnuje objekt řádku určený vlastností <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Každý nový řádek, který je klonován z šablony řádku, dostane svou vlastní kopii objektu stylu buňky šablony. Pro maximální škálovatelnost nastavte vlastnosti stylu buňky na úrovni <xref:System.Windows.Forms.DataGridView>. Nastavte například vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> spíše než vlastnost <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>.

- Pokud některé buňky vyžadují formátování jiné než výchozí formátování, použijte stejnou instanci <xref:System.Windows.Forms.DataGridViewCellStyle> napříč skupinami buněk, řádků nebo sloupců. Vyhněte se přímému nastavování vlastností typu <xref:System.Windows.Forms.DataGridViewCellStyle> pro jednotlivé buňky, řádky a sloupce. Příklad sdílení stylu buňky naleznete v tématu [How to: set pro ovládací prvek DataGridView ovládacího prvku model Windows Forms výchozí styly buněk](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Můžete se také vyhnout snížení výkonu při nastavení stylů buňky jednotlivě pomocí zpracování obslužné rutiny <xref:System.Windows.Forms.DataGridView.CellFormatting> události. Příklad naleznete v tématu [How to: Přizpůsobení formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Při určování stylu buňky použijte vlastnost <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> spíše než vlastnost <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>. Přístup k vlastnosti <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vytvoří novou instanci třídy <xref:System.Windows.Forms.DataGridViewCellStyle>, pokud vlastnost ještě není použitá. Kromě toho tento objekt nemusí obsahovat úplné informace o stylu buňky, pokud jsou některé styly zděděné z řádku, sloupce nebo ovládacího prvku. Další informace o dědičnosti stylu buňky naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Efektivní používání místních nabídek

Každá buňka, řádek a sloupec mohou mít vlastní místní nabídku. Místní nabídky v ovládacím prvku <xref:System.Windows.Forms.DataGridView> jsou reprezentovány <xref:System.Windows.Forms.ContextMenuStrip> ovládacími prvky. Stejně jako u objektů stylu buňky vytváření místních nabídek pro mnoho jednotlivých <xref:System.Windows.Forms.DataGridView> prvků má negativní vliv na výkon. Chcete-li se této sankci vyhnout, postupujte podle následujících pokynů:

- Vyhněte se vytváření místních nabídek pro jednotlivé buňky a řádky. To zahrnuje šablonu řádku, která je naklonována spolu s místní nabídkou, když jsou do ovládacího prvku přidány nové řádky. Pro maximální škálovatelnost použijte pouze vlastnost <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> ovládacího prvku k určení jedné místní nabídky pro celý ovládací prvek.

- Pokud požadujete více místních nabídek pro více řádků nebo buněk, zpracujte <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> nebo <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> události. Tyto události umožňují spravovat objekty místní nabídky sami, což vám umožní ladit výkon.

## <a name="using-automatic-resizing-efficiently"></a>Efektivní použití automatické změny velikosti

Řádky, sloupce a záhlaví lze automaticky změnit na velikost, protože se mění obsah buňky, aby byl celý obsah buněk zobrazen bez omezení. Změna režimů změny velikosti může také měnit velikost řádků, sloupců a záhlaví. Chcete-li určit správnou velikost, ovládací prvek <xref:System.Windows.Forms.DataGridView> musí prošetřit hodnotu každé buňky, kterou musí přizpůsobit. Při práci s velkými datovými sadami může tato analýza negativně ovlivnit výkon ovládacího prvku, když dojde k automatické změně velikosti. Chcete-li se vyhnout postihům výkonu, postupujte podle následujících pokynů:

- Nepoužívejte automatickou velikost ovládacího prvku <xref:System.Windows.Forms.DataGridView> s velkou sadou řádků. Pokud používáte automatickou velikost, stačí změnit velikost na základě zobrazených řádků. Používejte také zobrazené řádky ve virtuálním režimu.

  - Pro řádky a sloupce použijte pole `DisplayedCells` nebo `DisplayedCellsExceptHeaders` výčtů <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>a <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.

  - Pro záhlaví řádků použijte pole <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> nebo <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> výčtu <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>.

- Pro maximální škálovatelnost vypněte automatické určení velikosti a používejte programovou změnu velikosti.

Další informace najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGridView model Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Efektivní používání kolekcí vybraných buněk, řádků a sloupců

<xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce se neprovádí efektivně s velkými výběry. Kolekce <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> můžou být neefektivní, i když do menší míry, protože mezi buňkami v typickém ovládacím prvku <xref:System.Windows.Forms.DataGridView> existuje mnohem méně řádků, než jsou buňky, a mnoho sloupců než řádků. Chcete-li se vyhnout postihům na výkon při práci s těmito kolekcemi, postupujte podle následujících pokynů:

- Chcete-li určit, zda byly před přístupem k obsahu kolekce <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> vybrány všechny buňky ve <xref:System.Windows.Forms.DataGridView>, zkontrolujte vrácenou hodnotu metody <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. Upozorňujeme však, že tato metoda může způsobit, že se řádky nebudou sdílet. Další informace naleznete v následujícím oddílu.

- Vyhněte se použití vlastnosti <xref:System.Collections.ICollection.Count%2A> <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> k určení počtu vybraných buněk. Místo toho použijte metodu <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> a předejte hodnotu <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>. Podobně použijte metody <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> k určení počtu vybraných prvků místo přístupu k vybraným kolekcím řádků a sloupců.

- Nepoužívejte režimy výběru založené na buňkách. Místo toho nastavte vlastnost <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>Použití sdílených řádků

Efektivní využití paměti se dosahuje v ovládacím prvku <xref:System.Windows.Forms.DataGridView> prostřednictvím sdílených řádků. Řádky budou sdílet co nejvíce informací o jejich vzhledu a chování díky sdílení instancí třídy <xref:System.Windows.Forms.DataGridViewRow>.

Při sdílení instancí řádků ušetří paměť, řádky mohou být snadno nesdílené. Například pokaždé, když uživatel komunikuje přímo s buňkou, jeho řádek se nebude sdílet. Vzhledem k tomu, že se to nedá vyhnout, jsou pokyny v tomto tématu užitečné jenom při práci s velmi velkým objemem dat a jenom v případě, že uživatelé budou při každém spuštění programu pracovat s relativně malou částí dat.

Řádek nelze sdílet v nevázaném <xref:System.Windows.Forms.DataGridView> ovládacím prvku, pokud některá z jeho buněk obsahuje hodnoty. Když je ovládací prvek <xref:System.Windows.Forms.DataGridView> vázaný na externí zdroj dat nebo když implementujete virtuální režim a zadáte vlastní zdroj dat, hodnoty buněk jsou uloženy mimo ovládací prvek místo v objektech buňky, což umožňuje sdílení řádků.

Objekt řádku lze sdílet pouze v případě, že je možné určit stav všech jeho buněk ze stavu řádku a stavy sloupců, které obsahují buňky. Změníte-li stav buňky tak, aby již nelze odvodit ze stavu svého řádku a sloupce, řádek nelze sdílet.

Řádek nelze například sdílet v následujících situacích:

- Řádek obsahuje jednu vybranou buňku, která není ve vybraném sloupci.

- Řádek obsahuje buňku s nastavenou vlastností <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A>.

- Řádek obsahuje <xref:System.Windows.Forms.DataGridViewComboBoxCell> se sadou vlastností <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A>.

V vázaném režimu nebo ve virtuálním režimu můžete zadat popisy tlačítek a místní nabídky pro jednotlivé buňky, a to zpracováním <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> a <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>ch událostí.

Ovládací prvek <xref:System.Windows.Forms.DataGridView> se automaticky pokusí použít sdílené řádky pokaždé, když jsou do <xref:System.Windows.Forms.DataGridViewRowCollection>přidány řádky. Pokud chcete zajistit, aby se řádky sdílely, postupujte podle následujících pokynů:

- Vyhněte se volání `Add(Object[])` přetížení metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> a přetížení `Insert(Object[])` metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>. Tato přetížení automaticky vytvářejí nesdílené řádky.

- Ujistěte se, že řádek zadaný ve vlastnosti <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> lze sdílet v následujících případech:

  - Při volání `Add()` nebo `Add(Int32)` přetížení metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> nebo přetížení `Insert(Int32,Int32)` metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> kolekce.

  - Při zvýšení hodnoty vlastnosti <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>.

  - Při nastavování vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>.

- Ujistěte se, že řádek, který je určen parametrem `indexSource`, lze sdílet při volání metod <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>a <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

- Ujistěte se, že zadaný řádek nebo řádky lze sdílet při volání `Add(DataGridViewRow)` přetížení metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>, `Insert(Int32,DataGridViewRow)` přetížení metody <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> a metody <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

Chcete-li zjistit, zda je řádek sdílen, použijte metodu <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> pro načtení objektu řádku a poté zkontrolujte vlastnost <xref:System.Windows.Forms.DataGridViewBand.Index%2A> objektu. Sdílené řádky mají vždy hodnotu vlastnosti <xref:System.Windows.Forms.DataGridViewBand.Index%2A> – 1.

## <a name="preventing-rows-from-becoming-unshared"></a>Zabránění nesdílení řádků

Sdílené řádky se můžou stát nesdílením v důsledku kódu nebo akce uživatele. Abyste se vyhnuli dopadu na výkon, měli byste zabránit tomu, aby se řádky nesdílely. Během vývoje aplikace můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.RowUnshared> a určit, kdy se řádky stanou nesdílenými. To je užitečné při ladění problémů se sdílením řádků.

Pokud nechcete, aby se řádky staly nesdílenými, postupujte podle následujících pokynů:

- Vyhněte se indexování kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A> nebo ji pomocí smyčky `foreach` cyklicky iterace. Obvykle nebudete potřebovat přistupovat přímo k řádkům. <xref:System.Windows.Forms.DataGridView> metody, které pracují s řádky, převezmou argumenty indexu řádků místo instancí řádků. Kromě toho obslužné rutiny pro události související s řádky přijímají objekty argumentu události s vlastnostmi řádku, které lze použít k manipulaci s řádky, aniž by bylo nutné, aby se staly nesdílenými složkami.

- Pokud potřebujete přístup k objektu řádku, použijte metodu <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> a předejte si skutečný index řádku. Upozorňujeme však, že změna objektu sdíleného řádku načteného pomocí této metody změní všechny řádky, které sdílejí tento objekt. Řádek pro nové záznamy se ale nesdílí s jinými řádky, takže to ale nebude mít vliv na úpravu žádného jiného řádku. Všimněte si také, že různé řádky reprezentované sdíleným řádkem mohou mít různé místní nabídky. Chcete-li načíst správnou místní nabídku z instance sdíleného řádku, použijte metodu <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> a předejte jí skutečný index řádku. Pokud místo toho chcete získat přístup k vlastnosti <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> sdíleného řádku, použije se index sdíleného řádku o-1 a nebude načtena správná místní nabídka.

- Vyhněte se indexování kolekce <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>. Přímý přístup k buňce způsobí, že se její nadřazený řádek stane nesdíleným, vytvoří se instance nového <xref:System.Windows.Forms.DataGridViewRow>. Obslužné rutiny pro události související s buňkami přijímají objekty argumentu události s vlastnostmi buňky, které lze použít k manipulaci s buňkami, aniž by bylo nutné, aby se řádky nesdílely. Můžete také použít vlastnost <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> k načtení indexů řádků a sloupců aktuální buňky bez přístupu k buňce přímo.

- Nepoužívejte režimy výběru založené na buňkách. Tyto režimy způsobí, že dojde ke zrušení sdílení řádků. Místo toho nastavte vlastnost <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Nezpracovávat události <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>. Tyto události způsobí, že dojde ke zrušení sdílení řádků. Také Nevolejte <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ani <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> metody, které tyto události vyvolávají.

- Nepřístup do kolekce <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType>, pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. To způsobí, že se všechny vybrané řádky stanou nesdílenými.

- Nevolejte metodu <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>. Tato metoda může způsobit, že dojde ke zrušení sdílení řádků.

- Nevolejte metodu <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType>, pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Tím dojde k tomu, že se všechny řádky stanou nesdílenými.

- Nenastavte vlastnost <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> buňky na `false`, pokud je odpovídající vlastnost ve sloupci nastavena na `true`. Tím dojde k tomu, že se všechny řádky stanou nesdílenými.

- Nepřístup k vlastnosti <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>. Tím dojde k tomu, že se všechny řádky stanou nesdílenými.

- Nevolejte `Sort(IComparer)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A>. Řazení s vlastními porovnávacími způsobí, že se všechny řádky stanou nesdílenými.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md)
