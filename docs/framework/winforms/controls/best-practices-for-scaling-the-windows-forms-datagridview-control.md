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
ms.openlocfilehash: 91153df539871de571375d7bf6d49d712a0c43b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Doporučené postupy pro změnu velikosti v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení určená k poskytování maximální škálovatelnost. Pokud potřebujete zobrazit velké objemy dat, postupujte podle pokynů popsaných v tomto tématu, aby se zabránilo spotřebovává velké množství paměti nebo dlouhodobější snížení kvality odezvy uživatelského rozhraní (UI). Toto téma popisuje následující problémy:  
  
-   Efektivní použití styly buňky  
  
-   Efektivní použití místní nabídky  
  
-   Automatická změna velikosti efektivní použití  
  
-   Efektivní použití vybrané kolekce buněk, řádků a sloupců  
  
-   Použití sdílené řádky  
  
-   Brání stal odstranit řádky  
  
 Pokud máte speciální výkonu potřebám, můžete implementace virtuálního režimu a zadejte vlastní data operace správy. Další informace najdete v tématu [režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Efektivní použití styly buňky  
 Jednotlivých buněk, řádků a sloupců může mít svůj vlastní informace o stylu. Styl informace jsou uloženy v <xref:System.Windows.Forms.DataGridViewCellStyle> objekty. Vytváření objektů styl buněk pro mnoho jednotlivé <xref:System.Windows.Forms.DataGridView> elementy může být neefektivní, zejména při práci s velkými objemy dat. Abyste se vyhnuli vlivu na výkon, použijte následující pokyny:  
  
-   Vyhněte se nastavení vlastnosti styl buněk pro jednotlivé <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewRow> objekty. To zahrnuje objekt řádku určeného <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost. Každý nový řádek, který naklonována ze šablony řádku obdrží vlastní kopii objektu styl buněk šablony. Pro maximální škálovatelnost, nastavte vlastnosti styl buněk v <xref:System.Windows.Forms.DataGridView> úroveň. Například nastavit <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost místo <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> vlastnost.  
  
-   Pokud některé buňky potřebuje k formátování jiné než výchozí formátování, použijte stejný <xref:System.Windows.Forms.DataGridViewCellStyle> instance napříč skupiny buněk, řádků a sloupců. Vyhněte se přímo nastavení vlastnosti typu <xref:System.Windows.Forms.DataGridViewCellStyle> na jednotlivých buněk, řádků a sloupců. Příklad sdílení styl buněk, naleznete v části [postupy: nastavení výchozí styly buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Při nastavování styly buňky jednotlivě ve zpracování se můžete vyhnout snížení výkonu <xref:System.Windows.Forms.DataGridView.CellFormatting> obslužné rutiny události. Příklad, naleznete v části [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Při určování styl buněk, použijte <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> vlastnost místo <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> vlastnost. Přístup k <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost vytvoří novou instanci třídy <xref:System.Windows.Forms.DataGridViewCellStyle> třídy, pokud vlastnost nebyla už používá. Tento objekt navíc nemusí obsahovat informace o dokončení stylu pro buňky, pokud jsou některé styly zděděn z řádků, sloupců nebo řízení. Další informace o dědičnosti styl buněk najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Efektivní použití místní nabídky  
 Jednotlivých buněk, řádků a sloupců může mít svůj vlastní místní nabídky. Místní nabídky v <xref:System.Windows.Forms.DataGridView> řízení jsou reprezentované pomocí <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky. Stejně jako s objekty styl buněk, vytváření místních nabídek pro mnoho jednotlivé <xref:System.Windows.Forms.DataGridView> prvky budou mít negativní vliv na výkon. Abyste se vyhnuli toto snížení, použijte následující pokyny:  
  
-   Vyhněte se vytváření místních nabídek pro jednotlivých buněk a řádky. To zahrnuje řádku šablony, která je při přidávání řádků do ovládacího prvku klonovat společně s jeho místní nabídky. Pro maximální škálovatelnost, použijte pouze ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnosti a určit jeden místní nabídku pro celý ovládací prvek.  
  
-   Pokud budete potřebovat několik místních nabídek pro více řádků nebo buněk, je potřeba <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> nebo <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> události. Tyto události umožňují spravovat objekty nabídky zástupce sami, což umožňuje optimalizaci výkonu.  
  
## <a name="using-automatic-resizing-efficiently"></a>Automatická změna velikosti efektivní použití  
 Řádky, sloupce a hlavičky můžete automaticky nastavena velikost jako změny obsahu buněk, které budou zobrazeny celý obsah buňky bez výstřižek. Změna režimů změny velikosti můžete taky změnit velikost řádky, sloupce a hlavičky. K určení správnou velikost, <xref:System.Windows.Forms.DataGridView> řízení musí zkontrolujte hodnotu jednotlivých buněk, které musí zohlednit. Při práci s velkých datových sad, této analýze Automatická změna velikosti případě negativně ovlivnit výkon ovládacího prvku. Aby nedošlo k penalizaci výkonu, použijte následující pokyny:  
  
-   Nepoužívejte Automatická změna velikosti na <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí velké sady řádků. Pokud používáte Automatická změna velikosti, pouze změny velikosti podle zobrazených řádků. Použijte pouze zobrazených řádků v i virtuální režim.  
  
    -   Pro řádky a sloupce, použijte `DisplayedCells` nebo `DisplayedCellsExceptHeaders` pole z <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, a <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> výčty.  
  
    -   Záhlaví řádků, použijte <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> nebo <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> pole z <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> výčtu.  
  
-   Pro maximální škálovatelnost vypněte Automatická změna velikosti a používání Programová změna velikosti.  
  
 Další informace najdete v tématu [možnosti pro změnu velikosti v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Efektivní použití vybraných buněk, řádků a sloupců kolekce  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Kolekce neprovádí efektivně se velké výběry. <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekce může být také neefektivní, i když k v menší míře protože nejsou k dispozici mnoho méně řádků než buněk v typické <xref:System.Windows.Forms.DataGridView> řízení a mnoho méně sloupců, než řádků. Aby nedošlo k penalizaci výkon při práci s těchto kolekcí, použijte následující pokyny:  
  
-   K určení zda v buňkách v <xref:System.Windows.Forms.DataGridView> vybraných před přístup k obsahu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekce, zkontrolujte návratovou hodnotu <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metoda. Upozorňujeme však, že tato metoda může způsobit řádky se nesdílené. Další informace naleznete v následujícím oddílu.  
  
-   Nepoužívejte <xref:System.Collections.ICollection.Count%2A> vlastnost <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> k určení počtu vybraných buněk. Místo toho použijte <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> metoda a předejte jí <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> hodnotu. Podobně lze použít <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> metody k určení počtu vybraných elementů, nikoli přístup k vybraným kolekcím řádků a sloupců.  
  
-   Vyhněte se režimy výběru na základě buňky. Místo toho nastavte <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Používání sdíleného řádků  
 Je dosaženo pomocí využití efektivní paměti <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím sdílené řádky. Řádky budou sdílet co nejvíce informací o jejich vzhled a chování při sdílení instance <xref:System.Windows.Forms.DataGridViewRow> třídy.  
  
 Při sdílení instance řádek, že šetří paměť, může stát řádky snadno nesdílené. Například pokaždé, když uživatel komunikuje přímo s buňku, jeho řádek bude nesdílené. Protože to se nelze vyhnout spojení, podle pokynů v tomto tématu jsou užitečné pouze při práci s velmi velké objemy dat a pouze v případě, že uživatelé budou komunikovat s relativně malou část dat při každém spuštění programu.  
  
 Řádek nelze sdílet v nevázaný <xref:System.Windows.Forms.DataGridView> řídí, zda všechny jeho buněk obsahovat hodnoty. Když <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán k externímu zdroji dat nebo když implementace virtuálního režimu a zadejte vlastní zdroj dat, mají vzít hodnoty buněk jsou uložené mimo ovládací prvek, ne jako objekty buňky, což řádky, které se sdílet.  
  
 Objekt řádku lze sdílet pouze v případě, že stav všech jeho buněk lze určit stav řádku a stavy sloupců obsahujících buněk. Pokud změníte stav buňky tak, aby ho už být odvozen z stav jeho řádků a sloupců, řádek nelze sdílet.  
  
 Například řádek nelze sdílet v následujících situacích:  
  
-   Řádek obsahuje jedinou vybrané buňku, která není ve vybraném sloupci.  
  
-   Řádek obsahuje buňky s jeho <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> sadu vlastností.  
  
-   Obsahuje řádek <xref:System.Windows.Forms.DataGridViewComboBoxCell> s jeho <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> sadu vlastností.  
  
 V režimu vázané nebo virtuální, můžete zadat popisy tlačítek a místní nabídky pro jednotlivých buněk ve zpracování <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> a <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> události.  
  
 <xref:System.Windows.Forms.DataGridView> Řízení se automaticky pokusí použít sdílené řádky vždy, když jsou do přidán počet řádků <xref:System.Windows.Forms.DataGridViewRowCollection>. Pomocí následujících pokynů k zajištění, že jsou sdílené řádky:  
  
-   Vyhněte se volání `Add(Object[])` přetížení z <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metoda a `Insert(Object[])` přetížení z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metodu <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce. Tato přetížení automaticky vytvoří nesdílené řádků.  
  
-   Ujistěte se, který obsahuje řádek v <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnost lze sdílet v následujících případech:  
  
    -   Při volání metody `Add()` nebo `Add(Int32)` přetížení <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metoda nebo `Insert(Int32,Int32)` přetížení z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metodu <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce.  
  
    -   Když se hodnotu zvýšit <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Při nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> vlastnost.  
  
-   Ujistěte, zda řádek indikován `indexSource` parametr je možné sdílet při volání metody <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, a <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> metody <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> kolekce.  
  
-   Ujistěte se, že zadaný řádek nebo řádky je možné sdílet při volání metody `Add(DataGridViewRow)` přetížení z <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> metoda, <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> metody `Insert(Int32,DataGridViewRow)` přetížení z <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> metoda a <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> metoda <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>kolekce.  
  
 Chcete-li zjistit, zda je sdílen řádek, použijte <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metoda načíst objekt řádku a potom zkontrolujte objektu <xref:System.Windows.Forms.DataGridViewBand.Index%2A> vlastnost. Sdílené řádky mít vždy <xref:System.Windows.Forms.DataGridViewBand.Index%2A> vlastnost hodnotu -1.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Brání stal odstranit řádky  
 Sdílené řádky se může stát nesdílené v důsledku kódu nebo akce uživatele. Abyste se vyhnuli vlivu na výkon, neměli byste způsobuje řádky se nesdílené. Během vývoje aplikace dokáže zpracovat <xref:System.Windows.Forms.DataGridView.RowUnshared> událostí k určení, kdy začnou nesdílené řádků. To je užitečné při ladění problémů sdílení řádků.  
  
 Chcete-li zabránit vzniku odstranit řádky, použijte následující pokyny:  
  
-   Vyhněte se indexování <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce nebo iterace v rámci její `foreach` smyčky. Obvykle nebudete potřebovat pro přístup k řádky přímo. <xref:System.Windows.Forms.DataGridView> metody, které působí na řádky trvat řádek indexu argumenty spíš než řádek instance. Obslužné rutiny pro události související se řádek navíc zobrazí objektů argument událostí s vlastnostmi řádků, které můžete použít k manipulaci s řádky, aniž by to způsobilo, aby se mohly stát nesdílené.  
  
-   Pokud potřebujete přístup k objektu řádku, použijte <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> metoda a předejte jí skutečné index řádku. Upozorňujeme však, že změnit objekt sdíleného řádku načteny prostřednictvím této metody slouží k úpravě všechny řádky, které sdílejí tento objekt. Řádek pro nové záznamy není sdílený s další řádky, ale tak nebude mít vliv, pokud upravíte ostatních řádků. Všimněte si také, že různé řádky reprezentována sdíleného řádku může mít jiný místní nabídky. Pro načtení správné místní nabídky z instance sdíleného řádku, použijte <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> metoda a předejte jí skutečné index řádku. Pokud máte přístup k sdíleného řádku <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> vlastnost místo toho použije index sdíleného řádku-1 a nebudou načteny správné místní nabídky.  
  
-   Vyhněte se indexování <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> kolekce. Přístup k buňku přímo způsobí, že jeho nadřazeného řádku stane nesdílené, vytváření instancí nový <xref:System.Windows.Forms.DataGridViewRow>. Obslužné rutiny pro události související s buňky přijímat události argument objekty s vlastnosti buněk, které můžete použít k manipulaci s buněk, aniž by to způsobilo řádky se nesdílené. Můžete také <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> vlastnost načtení aktuální buňky indexy řádků a sloupců bez přístupu k buňky přímo.  
  
-   Vyhněte se režimy výběru na základě buňky. Tyto režimy způsobit řádky se nesdílené. Místo toho nastavte <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
-   Nezpracuje <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> události. Tyto události způsobit řádky se nesdílené. Navíc Nevolejte <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> metody, které vyvolávají tyto události.  
  
-   K přístupu ke <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> kolekce při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. To způsobí, že všechny vybrané řádky se nesdílené.  
  
-   Nevolejte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> metoda. Tato metoda může způsobit řádky se nesdílené.  
  
-   Nevolejte <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> metoda při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. To způsobí, že všechny řádky se nesdílené.  
  
-   Nenastavujte <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> nebo <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> vlastnost buňky do `false` když je odpovídající vlastnost v jeho sloupec nastavena na `true`. To způsobí, že všechny řádky se nesdílené.  
  
-   K přístupu ke <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> vlastnost. To způsobí, že všechny řádky se nesdílené.  
  
-   Nevolejte `Sort(IComparer)` přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda. Řazení s vlastní porovnávací funkci způsobí, že všechny řádky se nesdílené.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Virtuální režim v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
