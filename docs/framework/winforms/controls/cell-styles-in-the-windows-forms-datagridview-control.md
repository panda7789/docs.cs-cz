---
title: Styly buňky v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 3cb46ec5b203451cb2f9fd1c87457ad52552359c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674676"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Styly buňky v ovládacím prvku Windows Forms DataGridView
Každá buňka v rámci <xref:System.Windows.Forms.DataGridView> ovládací prvek může mít svůj vlastní styl, jako je například textovém formátu, barvu pozadí, barvu popředí a písma. Však obvykle více buněk sdílet vlastnosti konkrétního stylu.  
  
 Skupiny buněk, které sdílejí styly může zahrnovat všechny buňky v rámci konkrétní řádky nebo sloupce, všechny buňky, které obsahují konkrétní hodnoty nebo všechny buňky v ovládacím prvku. Protože tyto skupiny se překrývají, každá buňka může získat informace o stylu z více než jednom místě. Například můžete všechny buňky <xref:System.Windows.Forms.DataGridView> ovládací prvek a použít stejné písmo, ale pouze buňky v měně sloupce, které chcete použít formát měny a pouze měny buňky s záporná čísla Pokud chcete použít barvu popředí červené.  
  
## <a name="the-datagridviewcellstyle-class"></a>The DataGridViewCellStyle Class  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Třída obsahuje následující vlastnosti související s vizuálního stylu:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Tato třída také obsahuje následující vlastnosti související s formátování:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Další informace o těchto vlastností a další vlastnosti styl buňky, najdete v článku <xref:System.Windows.Forms.DataGridViewCellStyle> referenční dokumentaci a v tématech uvedených v následující části Viz také.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Použití objektů ovládací prvek DataGridViewCellStyle  
 Můžete načíst <xref:System.Windows.Forms.DataGridViewCellStyle> objekty z různých vlastností <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, a <xref:System.Windows.Forms.DataGridViewCell> třídy a jejich odvozené třídy. Pokud některou z těchto vlastností dosud nebyl nastaven, načítání jeho hodnoty vytvoří nový <xref:System.Windows.Forms.DataGridViewCellStyle> objektu. Můžete také vytvořit instanci vlastní <xref:System.Windows.Forms.DataGridViewCellStyle> objektů a přiřadit tyto vlastnosti.  
  
 Můžete se vyhnout zdvojení informací o stylu sdílení <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč několika <xref:System.Windows.Forms.DataGridView> elementy. Protože styly nastavit na ovládací prvek, sloupec nebo řádek úrovně vyfiltrovat prostřednictvím každou úroveň na úrovni buněk, můžete také vyhnout duplikaci styl nastavením pouze vlastnosti stylu na všech úrovních, která se liší od úrovně výše. To je popsána podrobněji vysvětlený v následující části dědičnost stylů.  
  
 V následující tabulce jsou uvedeny primární vlastnosti, které získání nebo nastavení <xref:System.Windows.Forms.DataGridViewCellStyle> objekty.  
  
|Vlastnost|Třídy|Popis|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>a odvozené třídy|Získá nebo nastaví výchozí styly využívané prostředím všechny buňky v celý ovládací prvek (včetně buněk záhlaví), ve sloupci nebo řádku.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používají všechny řádky v ovládacím prvku. To nezahrnuje buňky záhlaví.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané střídavé řádky v ovládacím prvku. Použít k vytvoření efektu účetní knihy.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané záhlaví řádků ovládacího prvku. Přepsat aktuální motiv, pokud jsou vizuální styly povoleny.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Získá nebo nastaví výchozích stylů buňky používané ovládacího prvku záhlaví sloupců. Přepsat aktuální motiv, pokud jsou vizuální styly povoleny.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> a odvozené třídy|Získává nebo nastavuje styly definované na úrovni buňky. Tyto styly mají přednost před akcemi zděděno z vyšší úrovně.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>a odvozené třídy|Získá všechny styly aktuálně použité na buňku, řádek nebo sloupec, včetně stylů, zděděno z vyšší úrovně.|  
  
 Jak je uvedeno výše, získání hodnoty vlastnosti stylu automaticky vytvoří nové <xref:System.Windows.Forms.DataGridViewCellStyle> objektu, pokud dříve nebyla nastavena vlastnost. Vyhnout se zbytečnému vytváření těchto objektů, řádků a sloupců třídy mají <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> vlastnost, která můžete zkontrolovat, určete, zda <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> byla nastavena vlastnost. Podobně buňky třídy mají <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> vlastnost, která označuje, zda <xref:System.Windows.Forms.DataGridViewCell.Style%2A> byla nastavena vlastnost.  
  
 Vlastnosti stylu má odpovídající *PropertyName* `Changed` událostí na <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pro řádků, sloupců a vlastnosti buněk, název události začíná řetězcem "`Row`","`Column`", nebo "`Cell`" (například <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Každá z těchto událostí nastane, pokud je odpovídající vlastnost stylu nastavena na jiný <xref:System.Windows.Forms.DataGridViewCellStyle> objektu. Tyto události se nevyskytují při načtení <xref:System.Windows.Forms.DataGridViewCellStyle> objektu z vlastnost stylu a upravit jeho hodnotám vlastností. Reakce na změny v samotných objektech styl buňky, zpracovat <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> událostí.  
  
## <a name="style-inheritance"></a>Dědičnost stylů  
 Každý <xref:System.Windows.Forms.DataGridViewCell> získá její vzhled z jeho <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost. <xref:System.Windows.Forms.DataGridViewCellStyle> Tato vlastnost vrátí objekt dědí jeho hodnoty z hierarchie vlastnosti typu <xref:System.Windows.Forms.DataGridViewCellStyle>. Tyto vlastnosti jsou uvedeny níže v pořadí, ve kterém <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> buňky bez záhlaví získá jeho hodnoty.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (pouze pro buňky řádků s lichá čísla indexu)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro buňky záhlaví řádků a sloupců <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost je vyplněn hodnoty z následujícího seznamu vlastností zdroje v uvedeném pořadí.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> Nebo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Následující diagram znázorňuje tento proces.  
  
 ![Vlastnosti typu ovládací prvek DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "diagram DataGridViewCells dědičnosti")  
  
 Můžete také přistupovat styly děděné konkrétní řádky a sloupce. Sloupec <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> vlastnost dědí jeho hodnoty z následující vlastnosti.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Řádek <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> vlastnost dědí jeho hodnoty z následující vlastnosti.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (pouze pro buňky řádků s lichá čísla indexu)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Pro každou vlastnost v <xref:System.Windows.Forms.DataGridViewCellStyle> vrácený `InheritedStyle` vlastnost, hodnota vlastnosti se získá z první styl buňky v příslušném seznamu, který má odpovídající vlastnost nastavena na hodnotu jiné než <xref:System.Windows.Forms.DataGridViewCellStyle> třídy výchozí hodnoty.  
  
 Následující tabulka ukazuje, jak <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hodnota vlastnosti u buněk příklad je zděděno z jeho obsahující sloupec.  
  
|vlastnost typu `DataGridViewCellStyle`|Příklad `ForeColor` hodnota načtený objektu|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 V takovém případě <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> hodnotu z buňky řádku je první skutečné hodnoty v seznamu. Toto řešení je <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> hodnota vlastnosti sady na buňku <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 Následující diagram znázorňuje, jak různé <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnosti může dědit jejich hodnoty z různých míst.  
  
 ![Vlastnost ovládacího prvku DataGridView&#45;hodnota dědičnosti](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells hodnota dědičnosti diagramu")  
  
 S využitím dědičnost stylů, můžete zadat odpovídající styly pro celý ovládací prvek bez nutnosti zadávat stejné informace na více místech.  
  
 I když buňky záhlaví se zapojují do dědičnosti styl, jak je popsáno, objektů vrácených <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> vlastnosti <xref:System.Windows.Forms.DataGridView> počáteční hodnoty vlastností, které přepisují hodnoty vlastností objektů vrácené objektem mít ovládací prvek <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost. Pokud chcete vlastnosti nastavit pro objekt vrácený rutinou <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost má použít pro záhlaví řádků a sloupců, odpovídající vlastnosti objektů vrácených podle musíte nastavit <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> uvedené vlastnosti na výchozí hodnoty pro <xref:System.Windows.Forms.DataGridViewCellStyle> třídy.  
  
> [!NOTE]
>  Pokud jsou povolené vizuální styly, záhlaví řádků a sloupců (s výjimkou <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) jsou automaticky ve stylu podle aktuálního motivu přepsání všechny styly podle těchto vlastností.  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, A <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> typy také inicializuje některé hodnoty objekt vrácený rutinou sloupci <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> vlastnost. Další informace naleznete v referenční dokumentaci pro tyto typy.  
  
## <a name="setting-styles-dynamically"></a>Nastavení stylů dynamicky  
 Pokud chcete upravit styly buňky s konkrétní hodnoty, implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí. Obslužné rutiny pro tuto událost přijímat argument <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> typu. Tento objekt obsahuje vlastnosti, které vám umožňují určit hodnotu buňka spolu s jeho umístění v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Tento objekt obsahuje také <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> vlastnost, která je inicializována na hodnotu <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost buňky chystáte formátovat. Můžete upravit vlastnosti stylu buňky k zadání informací o stylu odpovídající hodnota buňky a umístění.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> a <xref:System.Windows.Forms.DataGridView.RowPostPaint> také přijímat události <xref:System.Windows.Forms.DataGridViewCellStyle> data události objektu, ale v jejich případě jde o kopii řádku <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> vlastnost pro účely jen pro čtení a změny nemají vliv na ovládacím prvku.  
  
 Můžete taky dynamicky upravit styly jednotlivých buněk v reakci na události, jako <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseLeave> události. Například v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellMouseEnter> událostí, můžete například uložit aktuální hodnota barvy pozadí buněk (načíst z buňky <xref:System.Windows.Forms.DataGridViewCell.Style%2A> vlastnost), nastavte ji na novou barvu, která bude po umístění ukazatele myši nad ním Zvýraznit buňku. V obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellMouseLeave> události, barvu pozadí pak můžete obnovit na původní hodnotu.  
  
> [!NOTE]
>  Ukládání do mezipaměti hodnoty uložené v buňky <xref:System.Windows.Forms.DataGridViewCell.Style%2A> je důležité, bez ohledu na to, zda je hodnota konkrétního stylu nastavena vlastnost. Pokud vyměňujete dočasně nastavení stylu, obnovení do původního stavu "Nenastaveno" zajistí, že buňky se zpět do dědění nastavení stylu z vyšší úrovně. Pokud je potřeba určit skutečný styl v platnosti bez ohledu na to, jestli je zděděná styl buňky, použijte na buňku <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> vlastnost.  
  
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
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
