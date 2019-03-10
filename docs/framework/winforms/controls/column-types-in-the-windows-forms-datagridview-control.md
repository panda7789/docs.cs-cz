---
title: Typy sloupců v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: 8fd3ad0da369702c2a5e27c0b8b9a39a71c372ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724567"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy sloupců v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek používá několik typů sloupce k zobrazení jeho informace a umožňují uživatelům změnit nebo přidat informace.  
  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> ovládací prvek a nastavit <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> vlastnost `true`, sloupce jsou automaticky generovány pomocí vhodné pro datové typy obsažené ve zdroji vazby dat typy sloupců výchozí.  
  
 Můžete také vytvořit instance kteréhokoli sloupce tříd sami a přidat je do kolekce vrácené <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost. Můžete vytvořit tyto instance pro použití jako nevázaného sloupce, nebo můžete ručně vytvořit vazbu je. Ručně svázané sloupce jsou užitečné, například když chcete nahradit automaticky generované sloupce jednoho typu. sloupec jiného typu.  
  
 Následující tabulka popisuje různé třídy sloupce k dispozici pro použití v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Použít s textové hodnoty. Automaticky generovat při vytváření vazby na čísly a textovými řetězci.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Použít s <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState> hodnoty. Automaticky generovat při vytváření vazby hodnoty těchto typů.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Slouží k zobrazení obrázků. Automaticky generovat při vytváření vazby na pole bajtů <xref:System.Drawing.Image> objektů, nebo <xref:System.Drawing.Icon> objekty.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Slouží k zobrazení tlačítka v buňkách. Nelze automaticky generovat při vytváření vazby. Obvykle se používá jako nevázaných sloupců.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Slouží k zobrazení v buňkách rozevírací seznamy. Nelze automaticky generovat při vytváření vazby. Obvykle vázané na data ručně.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Slouží k zobrazení odkazů v buňkách. Nelze automaticky generovat při vytváření vazby. Obvykle vázané na data ručně.|  
|Typ vlastního sloupce|Můžete vytvořit vlastní třídu sloupec děděním <xref:System.Windows.Forms.DataGridViewColumn> třída nebo některý z jeho odvozené třídy, které poskytují vlastní vzhled, chování nebo hostované ovládací prvky. Další informace najdete v tématu [jak: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Tyto typy sloupců jsou popsány podrobněji v následujících částech.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> Je typ sloupce pro obecné účely pro použití s textové hodnoty, jako je čísly a textovými řetězci. V režimu úprav <xref:System.Windows.Forms.TextBox> ovládacího prvku se zobrazí v aktivní buňky, povolíte uživatelům upravit její hodnotu.  
  
 Hodnoty buněk se automaticky převedou na řetězce k zobrazení. Vytvořit hodnotu buňky odpovídající typ dat se automaticky Parsuje hodnoty zadané nebo upravil uživatel. Tyto převody můžete upravit tak, že zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting> a <xref:System.Windows.Forms.DataGridView.CellParsing> události <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Typ dat hodnoty buňky sloupce je zadaný v <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> vlastnost sloupce.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> Se používá s <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState> hodnoty. <xref:System.Boolean> Zobrazí hodnoty jako stav dvou nebo tří stavů zaškrtávací políčka, závisí na hodnotě <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> vlastnost. Sloupec je vázána k <xref:System.Windows.Forms.CheckState> hodnot, <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> hodnota vlastnosti je `true` ve výchozím nastavení.  
  
 Obvykle hodnot v buňkách zaškrtávací políčko slouží pro úložiště, jako jsou všechna data, nebo pro provádění hromadné operace. Pokud chcete reagovat okamžitě, když uživatelé kliknou na zaškrtávací políčko buňky, můžete zpracovávat <xref:System.Windows.Forms.DataGridView.CellClick> události, ale tato událost se vyvolá, předtím, než se aktualizuje její hodnotu. Pokud potřebujete nové hodnoty v době, klepněte na tlačítko, jednou z možností je k výpočtu co očekávaná hodnota bude na základě aktuální hodnoty. Další možností je okamžitě potvrďte změnu a zpracovat <xref:System.Windows.Forms.DataGridView.CellValueChanged> události a reagovat na něj. K provedení změn, při kliknutí na buňku, je nutné zpracovat <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> událostí. V obslužné rutině, pokud aktuální buňka nachází zaškrtávací políčko, zavolejte <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> metoda a předejte jí <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> hodnotu.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> Slouží k zobrazení obrázků. Obrázek sloupce můžete vyplní automaticky ze zdroje dat, vyplní ručně pro nevázaných sloupců nebo vložené dynamicky obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí.  
  
 Automatické naplnění sloupce obrázku ze zdroje dat funguje s bajtových polí v různých formátech obrázků, včetně všech formátů podporovaných <xref:System.Drawing.Image> třídy a obrázek OLE formát používaný čtečkou Microsoft® Access a ukázkové databáze Northwind.  
  
 Ručně naplnění sloupce obrázku je užitečné, když chcete poskytovat funkce <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale s přizpůsobený vzhled. Dokáže zpracovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> události a reakce na kliknutí v rámci na buňku bitové kopie.  
  
 Naplnění buňky sloupce obrázku v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí je užitečné, když chcete poskytovat imagí pro počítané hodnoty nebo ve formátech,-bitové kopie. Například může obsahovat sloupec "Riziko" s řetězcové hodnoty jako `"high"`, `"middle"`, a `"low"` , kterou chcete zobrazit jako ikony. Alternativně můžete mít sloupec "Image", který obsahuje umístění bitové kopie, které musí být načteny místo binární obsah obrázků.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 S <xref:System.Windows.Forms.DataGridViewButtonColumn>, můžete zobrazit sloupec buňky, které obsahují tlačítka. To je užitečné, když chcete usnadníte uživatelům provádět akce na konkrétní záznamy, jako je například zadání objednávky nebo zobrazení podřízené záznamy v samostatném okně.  
  
 Tlačítko sloupce nejsou generovány při vázání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použijte tlačítko sloupce, můžete je vytvořit ručně a přidat je do kolekci vrácené poskytovatelem <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> vlastnost.  
  
 Můžete reagovat na kliknutí v buňkách tlačítko pomocí manipulace <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> událostí.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 S <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, můžete zobrazit sloupec buňky, které obsahují pole se seznamem rozevíracího seznamu. To je užitečné pro zadávání dat v polích, která mohou obsahovat pouze konkrétní hodnoty, jako je například sloupec kategorie produktů tabulky v ukázkové databázi Northwind.  
  
 Můžete naplnit rozevíracího seznamu, použít pro všechny buňky stejným způsobem by naplnit <xref:System.Windows.Forms.ComboBox> rozevíracího seznamu, buď ručně přes kolekci vrácené poskytovatelem <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> vlastnost, nebo pomocí vazby ke zdroji dat prostřednictvím <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti. Další informace najdete v tématu [ovládacího prvku ComboBox](combobox-control-windows-forms.md).  
  
 Buňka skutečné hodnoty lze svázat zdroj dat používaný <xref:System.Windows.Forms.DataGridView> ovládacího prvku tak, že nastavíte <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Sloupce pole se seznamem nejsou generovány při vázání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použití sloupce pole se seznamem, musíte je vytvořit ručně a přidat je do kolekci vrácené poskytovatelem <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 S <xref:System.Windows.Forms.DataGridViewLinkColumn>, můžete zobrazit sloupec buňky, které obsahují hypertextové odkazy. To je užitečné pro hodnoty adresy URL ve zdroji dat nebo jako alternativu ke sloupci tlačítek pro zvláštní chování, jako je například otevřete okno s podřízené záznamy.  
  
 Odkaz sloupce nejsou generovány při vázání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Použijte odkaz sloupce, můžete je vytvořit ručně a přidat je do kolekci vrácené poskytovatelem <xref:System.Windows.Forms.DataGridView.Columns%2A> vlastnost.  
  
 Můžete reagovat na kliknutí na odkazy ve zpracování <xref:System.Windows.Forms.DataGridView.CellContentClick> událostí. Tato událost se liší od <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellMouseClick> události, ke kterým dochází, když uživatel klikne na tlačítko kdekoli v buňce.  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> Třída poskytuje několik vlastností pro úpravu vzhledu odkazů před, během a po kliknutí.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Postupy: Práce se sloupci obrázků v ovládacím prvku Windows Forms DataGridView](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
