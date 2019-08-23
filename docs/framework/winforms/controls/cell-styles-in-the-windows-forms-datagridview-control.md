---
title: Styly buňky v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917756"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styly buňky v ovládacím prvku Windows Forms DataGridView
Každá buňka v <xref:System.Windows.Forms.DataGridView> ovládacím prvku může mít vlastní styl, jako je textový formát, barva pozadí, barva popředí a písmo. Obvykle ale více buněk bude sdílet konkrétní charakteristiky stylu.  
  
 Skupiny buněk, které sdílejí styly, mohou zahrnovat všechny buňky v určitých řádcích nebo sloupcích, všechny buňky, které obsahují konkrétní hodnoty, nebo všechny buňky v ovládacím prvku. Vzhledem k tomu, že se tyto skupiny překrývají, může každá buňka získat informace o stylu z více než jednoho místa. Například můžete chtít, aby každá buňka v <xref:System.Windows.Forms.DataGridView> ovládacím prvku používala stejné písmo, ale pouze buňky ve sloupcích Currency používaly formát měny a jenom buňky Currency se zápornými čísly, aby se použila červená barva popředí.  
  
## <a name="the-datagridviewcellstyle-class"></a>Třída ovládací prvek DataGridViewCellStyle  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída obsahuje následující vlastnosti související s vizuálním stylem:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Tato třída také obsahuje následující vlastnosti týkající se formátování:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Další informace o těchto vlastnostech a dalších vlastnostech stylu buňky naleznete <xref:System.Windows.Forms.DataGridViewCellStyle> v referenční dokumentaci a v tématech uvedených v části Viz také níže.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Použití objektů ovládací prvek DataGridViewCellStyle  
 Můžete <xref:System.Windows.Forms.DataGridViewCellStyle> načíst objekty z různých vlastností <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.DataGridViewCell> tříd,, <xref:System.Windows.Forms.DataGridViewRow>a a jejich odvozených tříd. Pokud jedna z těchto vlastností ještě není nastavená, načtením její hodnoty se vytvoří nový <xref:System.Windows.Forms.DataGridViewCellStyle> objekt. Můžete také vytvořit instanci vlastních <xref:System.Windows.Forms.DataGridViewCellStyle> objektů a přiřadit jim tyto vlastnosti.  
  
 Je možné vyhnout se zbytečnému duplikaci informací o stylu <xref:System.Windows.Forms.DataGridViewCellStyle> sdílením objektů <xref:System.Windows.Forms.DataGridView> mezi více prvky. Vzhledem k tomu, že styly nastavené na úrovni ovládacího prvku, sloupce a řádku jsou vyfiltrovány přes jednotlivé úrovně na úroveň buňky, můžete také vyhnout duplikování stylu nastavením pouze těch vlastností stylu na všech úrovních, které se liší od výše uvedených úrovní. Tato informace je podrobněji popsána v části dědičnost stylu, která následuje.  
  
 Následující tabulka obsahuje seznam primárních vlastností, které získávají nebo <xref:System.Windows.Forms.DataGridViewCellStyle> nastavují objekty.  
  
|Vlastnost|Třídy|Popis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>odvozené třídy, <xref:System.Windows.Forms.DataGridViewColumn>,a <xref:System.Windows.Forms.DataGridViewRow>|Získá nebo nastaví výchozí styly používané všemi buňkami v celém ovládacím prvku (včetně buněk záhlaví), ve sloupci nebo v řádku.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané všemi řádky ovládacího prvku. To nezahrnuje buňky hlaviček.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané střídavými řádky v ovládacím prvku. Slouží k vytvoření efektu podobného hlavní knihy.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané záhlavími řádků ovládacího prvku. Přepsáno aktuálním motivem, pokud jsou povoleny vizuální styly.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozí styly buněk používané záhlavími sloupců ovládacího prvku. Přepsáno aktuálním motivem, pokud jsou povoleny vizuální styly.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>a odvozené třídy|Získá nebo nastaví styly určené na úrovni buňky. Tyto styly přepíšou zděděné z vyšších úrovní.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>odvozené třídy, <xref:System.Windows.Forms.DataGridViewRow>,a <xref:System.Windows.Forms.DataGridViewColumn>|Načte všechny styly, které jsou aktuálně použity pro buňku, řádek nebo sloupec, včetně stylů děděných z vyšších úrovní.|  
  
 Jak je uvedeno výše, získání hodnoty vlastnosti Style automaticky vytvoří instanci nového <xref:System.Windows.Forms.DataGridViewCellStyle> objektu, pokud vlastnost nebyla dříve nastavena. Aby nedocházelo k vytváření těchto objektů zbytečně, třídy řádků a sloupců mají <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> vlastnost, kterou lze ověřit, chcete-li určit, <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> zda byla vlastnost nastavena. Podobně třídy buněk mají <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> vlastnost, která označuje, <xref:System.Windows.Forms.DataGridViewCell.Style%2A> zda byla vlastnost nastavena.  
  
 Každá z vlastností stylu má odpovídající událost *PropertyName* `Changed` na <xref:System.Windows.Forms.DataGridView> ovládacím prvku. V případě vlastností řádku, sloupce a buňky`Row`začíná název události znakem "", "`Column`" nebo "`Cell`" (například <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Každá z těchto událostí nastane, pokud je odpovídající vlastnost Style nastavena na jiný <xref:System.Windows.Forms.DataGridViewCellStyle> objekt. Tyto události se nevyskytují, když nanačítáte <xref:System.Windows.Forms.DataGridViewCellStyle> objekt z vlastnosti Style a upravíte jeho hodnoty vlastností. Chcete-li reagovat na změny v samotných objektech stylu buňky <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> , zpracujte událost.  
  
## <a name="style-inheritance"></a>Dědičnost stylů  
 Každé <xref:System.Windows.Forms.DataGridViewCell> získá jeho vzhled z jeho <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnosti. Objekt vrácený touto vlastností zdědí své hodnoty z hierarchie vlastností typu <xref:System.Windows.Forms.DataGridViewCellStyle>. <xref:System.Windows.Forms.DataGridViewCellStyle> Tyto vlastnosti jsou uvedeny níže v pořadí, ve kterém <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> jsou pro buňky neobsahující záhlaví získány hodnoty.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(jenom pro buňky v řádcích s lichými čísly indexů)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro buňky <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> záhlaví řádků a sloupců se vlastnost vyplní hodnotami z následujícího seznamu zdrojových vlastností v daném pořadí.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> Nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Tento proces je znázorněn na následujícím obrázku.  
  
 ![Vlastnosti typu ovládací prvek DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagram dědičnosti DataGridViewCell")  
  
 Můžete také použít styly zděděné konkrétními řádky a sloupci. Vlastnost Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> zdědí své hodnoty z následujících vlastností.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Vlastnost řádku <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> zdědí své hodnoty z následujících vlastností.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(jenom pro buňky v řádcích s lichými čísly indexů)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro každou vlastnost v <xref:System.Windows.Forms.DataGridViewCellStyle> objektu, který je vrácen `InheritedStyle` vlastností, je hodnota vlastnosti získána z prvního stylu buňky v příslušném seznamu, který má odpovídající vlastnost nastavenou na jinou hodnotu než <xref:System.Windows.Forms.DataGridViewCellStyle> výchozí nastavení třídy.  
  
 Následující tabulka ukazuje, jak <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> je hodnota vlastnosti pro ukázkovou buňku zděděna z jeho nadřazeného sloupce.  
  
|Vlastnost typu`DataGridViewCellStyle`|Ukázková `ForeColor` hodnota načteného objektu|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 V tomto případě <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> je hodnota z řádku buňky první skutečnou hodnotou v seznamu. Tato hodnota se <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> zobrazí jako hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>buňky.  
  
 Následující diagram znázorňuje, jak různé <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnosti mohou dědit jejich hodnoty z různých míst.  
  
 ![Dědičnost hodnoty&#45;vlastnosti DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Sedatagridviewcell – Diagram dědičnosti hodnot")  
  
 Využitím dědění stylu můžete poskytnout vhodné styly pro celý ovládací prvek bez nutnosti zadávat stejné informace na více místech.  
  
 I když jsou buňky záhlaví zapojeny do dědění stylu jak je popsáno, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> objekty <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vrácené vlastnostmi a <xref:System.Windows.Forms.DataGridView> vlastností ovládacího prvku mají počáteční hodnoty vlastností, které přepíší hodnoty vlastností objektu vráceného <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost. Chcete-li nastavit vlastnosti objektu, které mají být vráceny <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastností, které mají být použity pro záhlaví řádků a sloupců, je nutné nastavit odpovídající vlastnosti objektů vrácených <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> vlastnostmi a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> k uvedeným výchozím hodnotám. <xref:System.Windows.Forms.DataGridViewCellStyle> pro třídu.  
  
> [!NOTE]
> Pokud jsou povoleny vizuální styly, záhlaví řádků a sloupců (kromě pro <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky upravena aktuálním motivem a přepsaly se všechny styly, které tyto vlastnosti určily.  
  
 Typy <xref:System.Windows.Forms.DataGridViewButtonColumn> <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> , <xref:System.Windows.Forms.DataGridViewImageColumn>a takéinicializujíněkteréhodnotyobjektuvrácenéhovlastnostíColumn.<xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Další informace najdete v referenční dokumentaci pro tyto typy.  
  
## <a name="setting-styles-dynamically"></a>Dynamické nastavení stylů  
 Chcete-li přizpůsobit styly buněk konkrétními hodnotami, Implementujte obslužnou rutinu <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> pro událost. Obslužné rutiny této události obdrží argument <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Tento objekt obsahuje vlastnosti, které umožňují určit hodnotu formátované buňky společně s umístěním v <xref:System.Windows.Forms.DataGridView> ovládacím prvku. Tento objekt obsahuje <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> také vlastnost, která je inicializována na hodnotu <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnosti buňky, která je formátována. Vlastnosti stylu buňky lze upravit tak, aby určovaly informace o stylu odpovídající hodnotě a umístění buňky.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> Události <xref:System.Windows.Forms.DataGridView.RowPrePaint> a<xref:System.Windows.Forms.DataGridView.RowPostPaint> také dostanou objekt v datech události, ale v jejich případě se jedná o kopii vlastnosti řádku pro účely jen pro čtení a změny v ní neovlivňují ovládací prvek.  
  
 Můžete také dynamicky upravovat styly jednotlivých buněk v reakci na události, jako jsou <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> události a. <xref:System.Windows.Forms.DataGridView.CellMouseLeave> Například v obslužné rutině <xref:System.Windows.Forms.DataGridView.CellMouseEnter> události můžete uložit aktuální hodnotu barvy pozadí buňky (získanou prostřednictvím <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnosti buňky) a pak ji nastavit na novou barvu, která zvýrazní buňku, když na ni ukazatel myši najede myší. V obslužné rutině pro <xref:System.Windows.Forms.DataGridView.CellMouseLeave> událost můžete obnovit barvu pozadí na původní hodnotu.  
  
> [!NOTE]
> Ukládání hodnot uložených ve <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnosti buňky do mezipaměti je důležité bez ohledu na to, zda je nastavena hodnota konkrétního stylu. Pokud dočasně nahradíte nastavení stylu a obnovíte ho do původního stavu Nenastaveno, zajistíte tak, že se buňka vrátí k dědění nastavení stylu z vyšší úrovně. Pokud potřebujete určit skutečný styl platný pro buňku bez ohledu na to, zda je styl zděděn, použijte <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost buňky.  
  
## <a name="see-also"></a>Viz také:

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
- [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](data-formatting-in-the-windows-forms-datagridview-control.md)
