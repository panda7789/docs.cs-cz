---
title: Styly buněk v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: fe56033a5adbe7719c64695c8f9ebc4f3644fc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746153"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styly buňky v ovládacím prvku Windows Forms DataGridView
Každá buňka v ovládacím prvku <xref:System.Windows.Forms.DataGridView> může mít vlastní styl, jako je textový formát, barva pozadí, barva popředí a písmo. Obvykle ale více buněk bude sdílet konkrétní charakteristiky stylu.  
  
 Skupiny buněk, které sdílejí styly, mohou zahrnovat všechny buňky v určitých řádcích nebo sloupcích, všechny buňky, které obsahují konkrétní hodnoty, nebo všechny buňky v ovládacím prvku. Vzhledem k tomu, že se tyto skupiny překrývají, může každá buňka získat informace o stylu z více než jednoho místa. Například můžete chtít, aby každá buňka v ovládacím prvku <xref:System.Windows.Forms.DataGridView> používala stejné písmo, ale pouze buňky ve sloupcích měny mají použít formát měny a jenom buňky Currency se zápornými čísly pro použití červené barvy popředí.  
  
## <a name="the-datagridviewcellstyle-class"></a>Třída ovládací prvek DataGridViewCellStyle  
 Třída <xref:System.Windows.Forms.DataGridViewCellStyle> obsahuje následující vlastnosti související s vizuálním stylem:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Tato třída také obsahuje následující vlastnosti týkající se formátování:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Další informace o těchto vlastnostech a dalších vlastnostech stylu buňky naleznete v <xref:System.Windows.Forms.DataGridViewCellStyle> referenční dokumentaci a v tématech uvedených v části Viz také níže.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Použití objektů ovládací prvek DataGridViewCellStyle  
 Můžete načíst <xref:System.Windows.Forms.DataGridViewCellStyle> objekty z různých vlastností tříd <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>a <xref:System.Windows.Forms.DataGridViewCell> a jejich odvozených tříd. Pokud jedna z těchto vlastností ještě není nastavená, načtením její hodnoty se vytvoří nový objekt <xref:System.Windows.Forms.DataGridViewCellStyle>. Můžete také vytvořit instanci vlastních objektů <xref:System.Windows.Forms.DataGridViewCellStyle> a přiřadit jim tyto vlastnosti.  
  
 Je možné vyhnout se zbytečnému duplikaci informací o stylu sdílením <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více <xref:System.Windows.Forms.DataGridView> prvky. Vzhledem k tomu, že styly nastavené na úrovni ovládacího prvku, sloupce a řádku jsou vyfiltrovány přes jednotlivé úrovně na úroveň buňky, můžete také vyhnout duplikování stylu nastavením pouze těch vlastností stylu na všech úrovních, které se liší od výše uvedených úrovní. Tato informace je podrobněji popsána v části dědičnost stylu, která následuje.  
  
 Následující tabulka obsahuje seznam primárních vlastností, které získávají nebo nastavují <xref:System.Windows.Forms.DataGridViewCellStyle> objekty.  
  
|Vlastnost|Třídy|Popis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>a odvozené třídy|Získá nebo nastaví výchozí styly používané všemi buňkami v celém ovládacím prvku (včetně buněk záhlaví), ve sloupci nebo v řádku.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané všemi řádky ovládacího prvku. To nezahrnuje buňky hlaviček.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané střídavými řádky v ovládacím prvku. Slouží k vytvoření efektu podobného hlavní knihy.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané záhlavími řádků ovládacího prvku. Přepsáno aktuálním motivem, pokud jsou povoleny vizuální styly.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané záhlavími sloupců ovládacího prvku. Přepsáno aktuálním motivem, pokud jsou povoleny vizuální styly.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy|Získá nebo nastaví styly určené na úrovni buňky. Tyto styly přepíšou zděděné z vyšších úrovní.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>a odvozené třídy|Načte všechny styly, které jsou aktuálně použity pro buňku, řádek nebo sloupec, včetně stylů děděných z vyšších úrovní.|  
  
 Jak je uvedeno výše, získání hodnoty vlastnosti Style automaticky vytvoří instanci nového objektu <xref:System.Windows.Forms.DataGridViewCellStyle>, pokud vlastnost nebyla dříve nastavena. Chcete-li se vyhnout vytváření těchto objektů zbytečně, třídy řádků a sloupců mají vlastnost <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>, kterou lze ověřit a určit, zda byla nastavena vlastnost <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>. Podobně třídy buněk mají vlastnost <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>, která označuje, zda byla nastavena vlastnost <xref:System.Windows.Forms.DataGridViewCell.Style%2A>.  
  
 Každá z vlastností stylu má odpovídající událost *PropertyName*`Changed` v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. V případě vlastností řádku, sloupce a buňky začíná název události "`Row`", "`Column`" nebo "`Cell`" (například <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Každá z těchto událostí nastane, pokud je odpovídající vlastnost Style nastavena na jiný objekt <xref:System.Windows.Forms.DataGridViewCellStyle>. Tyto události se nevyskytují, když nanačítáte objekt <xref:System.Windows.Forms.DataGridViewCellStyle> z vlastnosti Style a upravíte jeho hodnoty vlastností. Chcete-li reagovat na změny v samotných objektech stylu buňky, zpracujte událost <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>.  
  
## <a name="style-inheritance"></a>Dědičnost stylů  
 Každé <xref:System.Windows.Forms.DataGridViewCell> získá jeho vzhled z jeho vlastnosti <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>. Objekt <xref:System.Windows.Forms.DataGridViewCellStyle> vrácený touto vlastností zdědí své hodnoty z hierarchie vlastností typu <xref:System.Windows.Forms.DataGridViewCellStyle>. Tyto vlastnosti jsou uvedené níže v pořadí, ve kterém <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> pro buňky neobsahují své hodnoty.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (jenom pro buňky v řádcích s lichými čísly indexu)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro buňky záhlaví řádků a sloupců se vlastnost <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vyplní hodnotami z následujícího seznamu zdrojových vlastností v daném pořadí.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Tento proces je znázorněn na následujícím obrázku.  
  
 ![Vlastnosti typu ovládací prvek DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagram dědičnosti DataGridViewCell")  
  
 Můžete také použít styly zděděné konkrétními řádky a sloupci. Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> sloupce zdědí své hodnoty z následujících vlastností.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Vlastnost <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> řádku zdědí své hodnoty z následujících vlastností.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (jenom pro buňky v řádcích s lichými čísly indexu)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro každou vlastnost v objektu <xref:System.Windows.Forms.DataGridViewCellStyle> vrácenou vlastností `InheritedStyle` je hodnota vlastnosti získána z prvního stylu buňky v příslušném seznamu, který má odpovídající vlastnost nastavenou na jinou hodnotu než výchozí hodnota třídy <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 Následující tabulka ukazuje, jak je hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> pro ukázkovou buňku zděděna z jeho nadřazeného sloupce.  
  
|Vlastnost typu `DataGridViewCellStyle`|Příklad `ForeColor` hodnoty pro načtený objekt|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 V tomto případě je hodnota <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>a z řádku buňky první skutečnou hodnotou v seznamu. Tím se hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>buňky.  
  
 Následující diagram znázorňuje, jak různé vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> mohou dědit jejich hodnoty z různých míst.  
  
 ![Dědičnost hodnoty&#45;vlastnosti DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Sedatagridviewcell – Diagram dědičnosti hodnot")  
  
 Využitím dědění stylu můžete poskytnout vhodné styly pro celý ovládací prvek bez nutnosti zadávat stejné informace na více místech.  
  
 I když jsou buňky záhlaví zapojeny do dědění stylu jak je popsáno, objekty vrácené <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastností ovládacího prvku <xref:System.Windows.Forms.DataGridView> mají počáteční hodnoty vlastností, které přepíší hodnoty vlastností objektu vráceného vlastností <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Chcete-li nastavit vlastnosti objektu, které jsou vráceny vlastností <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, aby byly použity pro záhlaví řádků a sloupců, je nutné nastavit odpovídající vlastnosti objektů vrácených <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastnosti do výchozích hodnot, které jsou uvedeny pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídu.  
  
> [!NOTE]
> Pokud jsou povoleny vizuální styly, záhlaví řádků a sloupců (kromě <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky upravena aktuálním motivem a přepsaly se všechny styly určené těmito vlastnostmi.  
  
 Typy <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>a <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> také inicializují některé hodnoty objektu vráceného vlastností sloupce <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>. Další informace najdete v referenční dokumentaci pro tyto typy.  
  
## <a name="setting-styles-dynamically"></a>Dynamické nastavení stylů  
 Chcete-li přizpůsobit styly buněk konkrétními hodnotami, Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Obslužné rutiny této události obdrží argument typu <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>. Tento objekt obsahuje vlastnosti, které umožňují určit hodnotu formátované buňky spolu s jejím umístěním v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Tento objekt obsahuje také vlastnost <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>, která je inicializována na hodnotu vlastnosti <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> buňky, která je formátována. Vlastnosti stylu buňky lze upravit tak, aby určovaly informace o stylu odpovídající hodnotě a umístění buňky.  
  
> [!NOTE]
> Události <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> také dostanou objekt <xref:System.Windows.Forms.DataGridViewCellStyle> v datech události, ale v jejich případě se jedná o kopii vlastnosti řádku <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> pro účely jen pro čtení a změny v ní neovlivňují ovládací prvek.  
  
 Můžete také dynamicky upravovat styly jednotlivých buněk v reakci na události, jako jsou <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseLeave> události. Například v obslužné rutině události <xref:System.Windows.Forms.DataGridView.CellMouseEnter> můžete uložit aktuální hodnotu barvy pozadí buňky (získanou prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridViewCell.Style%2A>) a pak ji nastavit na novou barvu, která zvýrazní buňku, když na ni ukazatel myši najede. V obslužné rutině události <xref:System.Windows.Forms.DataGridView.CellMouseLeave> lze obnovit barvu pozadí na původní hodnotu.  
  
> [!NOTE]
> Ukládání hodnot uložených v vlastnosti <xref:System.Windows.Forms.DataGridViewCell.Style%2A> buňky je důležité bez ohledu na to, jestli je nastavená hodnota konkrétního stylu. Pokud dočasně nahradíte nastavení stylu a obnovíte ho do původního stavu Nenastaveno, zajistíte tak, že se buňka vrátí k dědění nastavení stylu z vyšší úrovně. Pokud potřebujete určit skutečný styl platný pro buňku bez ohledu na to, zda je styl zděděn, použijte vlastnost <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> buňky.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
