---
title: Doporučené postupy pro změnu velikosti v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 234d29470d9b1c810e23c082a032d9a880b65fbd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635002"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Doporučené postupy pro změnu velikosti v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek je navrženo pro zajištění maximální škálovatelnosti. Pokud potřebujete zobrazit velké objemy dat, postupujte podle pokynů popsaných v tomto tématu, aby se zabránilo zpracovávání velké množství paměti a snížení rychlosti odezvy uživatelského rozhraní (UI). Toto téma popisuje následující problémy:  
  
- Efektivní využívání styly buňky  
  
- Efektivní využívání nabídek  
  
- Používat automatickou změnu velikosti efektivně  
  
- Efektivní využívání vybrané kolekce buněk, řádků a sloupců  
  
- Použití sdílené řádky  
  
- Brání stávají odstranit řádky  
  
 Pokud máte zvláštní výkon, můžete implementace virtuálního režimu a zadat vlastní operace správy data. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Efektivní využívání styly buňky  
 Každý buněk, řádků a sloupců může mít svůj vlastní informace o stylu. Styl informace jsou uloženy v <xref:System.Windows.Forms.DataGridViewCellStyle> objekty. Vytváření objektů styl buňky pro mnoho jednotlivých <xref:System.Windows.Forms.DataGridView> elementy může být neefektivní, zejména při práci s velkými objemy dat. Aby se zabránilo vlivu na výkon, použijte následující pokyny:  
  
- Vyhněte se nastavování vlastnosti stylu buňky jednotlivce <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewRow> objekty. Jedná se o objekt řádku určené <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost. Každý nový řádek, který naklonována ze šablony řádku obdrží vlastní kopii šablony objektu stylu buňky. Pro maximální rozšiřitelnost, nastavte vlastnosti stylu buňky v <xref:System.Windows.Forms.DataGridView> úroveň. Například nastavit <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost místo <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> vlastnost.  
  
- Pokud u některých buněk vyžadují jiné než výchozí formátování formátování, použijte stejný <xref:System.Windows.Forms.DataGridViewCellStyle> instance napříč skupinami buněk, řádků nebo sloupců. Vyhněte se přímo nastavení vlastnosti typu <xref:System.Windows.Forms.DataGridViewCellStyle> na jednotlivých buněk, řádků a sloupců. Příklad sdílení styl buňky, naleznete v tématu [jak: Nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Při nastavování stylů buňky samostatně pomocí manipulace se můžete vyhnout snížení výkonu <xref:System.Windows.Forms.DataGridView.CellFormatting> obslužné rutiny události. Příklad najdete v tématu [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
- Při určování styl buňky, použijte <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> vlastnost místo <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> vlastnost. Přístup k <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost vytvoří novou instanci třídy <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, pokud vlastnost ještě nebyl použit. Kromě toho tento objekt nemusí obsahovat informace o dokončení styl buňky, pokud některé styly jsou zděděny z řádků, sloupců nebo ovládacího prvku. Další informace o dědičnosti styl buňky, naleznete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Efektivní využívání nabídek  
 Každý buněk, řádků a sloupců může mít svůj vlastní místní nabídky. Místní nabídky v <xref:System.Windows.Forms.DataGridView> ovládacího prvku jsou reprezentovány <xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků. Stejně jako u objektů styl buňky, vytváření místních nabídek pro mnoho jednotlivých <xref:System.Windows.Forms.DataGridView> prvky budou mít negativní vliv na výkon. Abyste předešli této penalizace, použijte následující pokyny:  
  
- Vyhněte se vytváření místních nabídek pro jednotlivé buňky a řádků. To zahrnuje řádek šablony, která je klonovat spolu s jeho místní nabídku, při přidání nových řádků do ovládacího prvku. Pro maximální rozšiřitelnost, použijte pouze ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnosti a určit jeden místní nabídku pro celý ovládací prvek.  
  
- Pokud budete potřebovat více místních nabídek pro více řádcích nebo buňky, zpracovat <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> nebo <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> události. Tyto události vám umožní spravovat objekty místní nabídky sami, abyste mohli optimalizovat výkon.  
  
## <a name="using-automatic-resizing-efficiently"></a>Používat automatickou změnu velikosti efektivně  
 Řádky, sloupce a záhlaví můžete automaticky nastavena velikost při změně obsahu buňky, které veškerý obsah buňky budou zobrazeny bez oříznutí. Změna režimů změny velikosti můžete taky změnit velikost řádky, sloupce a záhlaví. K určení správné velikosti <xref:System.Windows.Forms.DataGridView> ovládací prvek musí zkoumat hodnoty jednotlivých buněk, které musí zohlednit. Při práci s velkými datovými sadami, tato analýza může mít negativní vliv na výkon ovládacího prvku dojde-li automatickou změnu velikosti. Aby se zabránilo snížení výkonu, použijte následující pokyny:  
  
- Nepoužívejte automatické velikosti na <xref:System.Windows.Forms.DataGridView> ovládací prvek s velkou sadu řádků. Pokud používáte automatické velikosti, pouze změny velikosti podle zobrazených řádků. Ve virtuálním režimu také použijte pouze zobrazených řádků.  
  
    - U řádků a sloupců, použijte `DisplayedCells` nebo `DisplayedCellsExceptHeaders` pole <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, a <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> výčty.  
  
    - Záhlaví řádků, použijte <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> nebo <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> pole <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> výčtu.  
  
- Pro maximální rozšiřitelnost vypněte automatické velikosti a používání Programová změna velikosti.  
  
 Další informace najdete v tématu [možnosti nastavení velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Efektivní využívání vybraných buněk, řádků a sloupců kolekce  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Kolekce neprovádí efektivně velké výběry. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce může být také neefektivní, i když se do menší míry vzhledem k tomu, že existují mnoho méně řádků než buněk v typické <xref:System.Windows.Forms.DataGridView> ovládacího prvku a řadu méně sloupců, než řádků. Aby se zabránilo snížení výkonu při práci s těchto kolekcí, použijte následující pokyny:  
  
- K určení, zda všechny buňky v <xref:System.Windows.Forms.DataGridView> byly vybrány před přístupem k obsahu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce, zkontrolovat návratovou hodnotu <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metody. Upozorňujeme však, že tato metoda může způsobit řádků, které mají být nejdříve zrušeno sdílení. Další informace naleznete v následujícím oddílu.  
  
- Vyhněte se použití <xref:System.Collections.ICollection.Count%2A> vlastnost <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> k určení počtu vybraných buněk. Místo toho použijte <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> metoda a předejte jí <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> hodnotu. Podobně lze použít <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> metody k určení počtu vybraných elementů, spíše než přístup k vybraným kolekcím řádků a sloupců.  
  
- Vyhněte se režimy výběru založené na buňky. Místo toho nastavte <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Použití sdílené řádky  
 Využití paměti efektivní je dosaženo <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím sdílené řádky. Řádky budou sdílet co nejvíce informací o jejich vzhled a chování při sdílení instance <xref:System.Windows.Forms.DataGridViewRow> třídy.  
  
 Při sdílení instance řádek šetří paměť, řádky se snadno můžou stát nejdříve zrušeno sdílení. Například pokaždé, když uživatel komunikuje přímo s buňky, jeho řádku stane nejdříve zrušeno sdílení. Protože to se nelze vyhnout spojení, pokyny v tomto tématu jsou užitečné pouze při práci s velmi velké objemy dat a pouze v případě, že uživatelé budou komunikovat s relativně malou část dat pokaždé, když spuštění programu.  
  
 Řádek nelze sdílet v nevázaný <xref:System.Windows.Forms.DataGridView> ovládací prvek, pokud některý z jeho buňky obsahovat hodnoty. Když <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán k externímu zdroji dat nebo když implementace virtuálního režimu a zadejte vlastní zdroj dat, mají vzít hodnoty buněk jsou uložené mimo ovládací prvek, nikoli v buňce objektům, umožňuje řádků, které chcete sdílet.  
  
 Objekt řádku je možné sdílet pouze pokud stavu všech jeho buněk lze určit stav řádku a stavy sloupců obsahujících buňky. Při změně stavu buňky, tak, aby ho už je možné odvodit z stav jeho řádku a sloupce, řádku nelze sdílet.  
  
 Například řádek nelze sdílet v některém z následujících situací:  
  
- Tento řádek obsahuje jedinou vybranou buňku, která není ve vybraném sloupci.  
  
- Tento řádek obsahuje buňku s jeho <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> set vlastnosti.  
  
- Tento řádek obsahuje <xref:System.Windows.Forms.DataGridViewComboBoxCell> s jeho <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> sadu vlastností.  
  
 V režimu vázané nebo virtuální, můžete zadat popisky a místní nabídky pro jednotlivé buňky pomocí manipulace <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> a <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> události.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek se automaticky pokusí použít sdílené řádky pokaždé, když jsou řádky přidány do <xref:System.Windows.Forms.DataGridViewRowCollection>. Pomocí následujících pokynů k zajištění, že jsou sdílené řádky:  
  
- Vyhněte se volání `Add(Object[])` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metoda a `Insert(Object[])` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metodu <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce. Tato přetížení automaticky vytvoří nesdílený řádků.  
  
- Ujistěte se, že řádek zadané v <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnost je možné sdílet v následujících případech:  
  
    - Při volání `Add()` nebo `Add(Int32)` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metoda nebo `Insert(Int32,Int32)` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metodu <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce.  
  
    - Když zvýšit hodnotu <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> vlastnost.  
  
    - Při nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> vlastnost.  
  
- Ujistěte se, že řádek označený `indexSource` parametr je možné sdílet při volání <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, a <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce.  
  
- Ujistěte se, že zadaný řádek nebo řádky je možné sdílet při volání `Add(DataGridViewRow)` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metody, <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> metody `Insert(Int32,DataGridViewRow)` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metoda a <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> metoda <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>kolekce.  
  
 Chcete-li zjistit, jestli je sdílené řádek, použijte <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> má metoda načíst objekt řádku a potom zkontrolujte objektu <xref:System.Windows.Forms.DataGridViewBand.Index%2A> vlastnost. Sdílené řádky vždy mít <xref:System.Windows.Forms.DataGridViewBand.Index%2A> vlastnost hodnota – 1.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Brání stávají odstranit řádky  
 Sdílené řádky se může stát nesdílený jako výsledek kódu nebo akce uživatele. Aby se zabránilo vlivu na výkon, byste se měli vyhnout způsobí řádků, které mají být nejdříve zrušeno sdílení. Během vývoje aplikace dokáže zpracovat <xref:System.Windows.Forms.DataGridView.RowUnshared> událostí k určení, kdy budou nejdříve zrušeno sdílení řádků. To je užitečné při ladění problémů sdílení řádků.  
  
 Abyste zabránili stávají odstranit řádky, použijte následující pokyny:  
  
- Vyhněte se indexování <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce nebo iterace s `foreach` smyčky. Obvykle nebudete potřebovat pro přístup k řádků přímo. <xref:System.Windows.Forms.DataGridView> metody, které pracují s řádky trvat argumenty index řádku, spíše než řádek instance. Obslužné rutiny pro události týkající se řádek navíc zobrazí objekty argumentu události s vlastnostmi řádků, které můžete použít k manipulaci s řádky, aniž by jim být nejdříve zrušeno sdílení.  
  
- Pokud potřebujete přístup k objektu řádku, použijte <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metoda a předejte jí skutečné index řádku. Všimněte si však, změnit objekt sdíleného řádku získat pomocí této metody bude měnit všechny řádky, které sdílejí tento objekt. Řádek pro nové záznamy nesdílí s další řádky, ale tak nebude mít vliv, pokud upravíte ostatních řádků. Všimněte si také, že různé řádky reprezentována sdíleného řádku může mít jinou místní nabídky. K získání správné místní nabídku z instance sdíleného řádku, použijte <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> metoda a předejte jí skutečné index řádku. Pokud přistupujete sdíleného řádku <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> vlastnost místo toho použije index sdíleného řádku-1 a nebudou načteny správné místní nabídce.  
  
- Vyhněte se indexování <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> kolekce. Přímý přístup buňky způsobí, že jeho nadřazený řádek se nejdříve zrušeno sdílení, vytvoření instance nového <xref:System.Windows.Forms.DataGridViewRow>. Obslužné rutiny pro události týkající se buňky přijímat události objekty argumentu s vlastnostmi buňky, které slouží k manipulaci s buňkami, aniž by to způsobilo řádků, které mají být nejdříve zrušeno sdílení. Můžete také použít <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> vlastnost pro načtení aktuální buňky řádků a sloupců indexy bez přístupu k buňce přímo.  
  
- Vyhněte se režimy výběru založené na buňky. Tyto režimy způsobit řádků, které mají být nejdříve zrušeno sdílení. Místo toho nastavte <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
- Ke zpracování <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> události. Tyto události způsobit řádků, které mají být nejdříve zrušeno sdílení. Navíc Nevolejte <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> metody, které vyvolávají tyto události.  
  
- Přístup <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> kolekce při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. To způsobí, že všechny vybrané řádky se nejdříve zrušeno sdílení.  
  
- Nevolejte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> metody. Tato metoda může způsobit řádků, které mají být nejdříve zrušeno sdílení.  
  
- Nevolejte <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> metoda při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. To způsobí, že všechny řádky budou nejdříve zrušeno sdílení.  
  
- Nenastavujte <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> vlastnost buňky do `false` když odpovídající v jeho sloupec je nastavena na `true`. To způsobí, že všechny řádky budou nejdříve zrušeno sdílení.  
  
- Přístup <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> vlastnost. To způsobí, že všechny řádky budou nejdříve zrušeno sdílení.  
  
- Nevolejte `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metody. Řazení s vlastní porovnávací metody způsobí, že všechny řádky budou nejdříve zrušeno sdílení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md)
