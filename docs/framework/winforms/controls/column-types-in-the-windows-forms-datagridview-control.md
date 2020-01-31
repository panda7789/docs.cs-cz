---
title: Typy sloupců v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743851"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Typy sloupců v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> pro zobrazení informací používá několik typů sloupců a umožňuje uživatelům upravovat nebo přidávat informace.  
  
 Když vytvoříte vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> a nastavíte vlastnost <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> na `true`, automaticky se vygenerují sloupce s použitím výchozích typů sloupců odpovídajících datovým typům obsaženým ve vázaném zdroji dat.  
  
 Můžete také vytvořit instance libovolné třídy sloupce sami a přidat je do kolekce vrácené vlastností <xref:System.Windows.Forms.DataGridView.Columns%2A>. Tyto instance můžete vytvořit pro použití jako nevázané sloupce nebo je můžete svázat ručně. Ručně vázané sloupce jsou užitečné, například když chcete nahradit automaticky generovaný sloupec jednoho typu sloupcem jiného typu.  
  
 Následující tabulka popisuje různé třídy sloupců, které jsou k dispozici pro použití v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Používá se s hodnotami založenými na textu. Generuje se automaticky při vazbě na čísla a řetězce.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Používá se s hodnotami <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState>. Generuje se automaticky při vytváření vazby na hodnoty těchto typů.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Slouží k zobrazení obrázků. Generováno automaticky při vázání na pole bajtů, <xref:System.Drawing.Image> objektů nebo objektů <xref:System.Drawing.Icon>.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Slouží k zobrazení tlačítek v buňkách. Negeneruje se automaticky při vazbě. Obvykle se používá jako nevázané sloupce.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Slouží k zobrazení rozevíracích seznamů v buňkách. Negeneruje se automaticky při vazbě. Obvykle se datově sváže ručně.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Slouží k zobrazení odkazů v buňkách. Negeneruje se automaticky při vazbě. Obvykle se datově sváže ručně.|  
|Vlastní typ sloupce|Můžete vytvořit vlastní třídu sloupce děděním <xref:System.Windows.Forms.DataGridViewColumn> třídy nebo kterékoli z jeho odvozených tříd, a poskytnout tak vlastní vzhled, chování nebo hostované ovládací prvky. Další informace najdete v tématu [Postup: přizpůsobení buněk a sloupců v ovládacím prvku DataGridView model Windows Forms rozšířením jejich chování a vzhledu.](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Tyto typy sloupců jsou podrobněji popsány v následujících částech.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> je typ sloupce pro obecné účely pro použití s textovými hodnotami, jako jsou čísla a řetězce. V režimu úprav je ovládací prvek <xref:System.Windows.Forms.TextBox> zobrazen v aktivní buňce a umožňuje uživatelům změnit hodnotu buňky.  
  
 Hodnoty buněk jsou automaticky převedeny na řetězce pro zobrazení. Hodnoty zadané nebo upravené uživatelem se automaticky analyzují, aby se vytvořila hodnota buňky příslušného datového typu. Tyto převody lze přizpůsobit zpracováním <xref:System.Windows.Forms.DataGridView.CellFormatting> a <xref:System.Windows.Forms.DataGridView.CellParsing> událostí ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
 Datový typ hodnota buňky sloupce je zadán ve vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> sloupce.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> se používá s hodnotami <xref:System.Boolean> a <xref:System.Windows.Forms.CheckState>. hodnoty <xref:System.Boolean> se v závislosti na hodnotě vlastnosti <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> zobrazují jako dvě nebo tři stavy. Když je sloupec vázaný na <xref:System.Windows.Forms.CheckState> hodnoty, ve výchozím nastavení je hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> `true`.  
  
 Hodnoty buněk zaškrtávacího políčka jsou obvykle určené pro úložiště, stejně jako jakákoli jiná data nebo pro provádění hromadných operací. Pokud chcete ihned reagovat, když uživatel klikne na buňku zaškrtávacího políčka, můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.CellClick>, ale tato událost nastane před aktualizací hodnoty buňky. Pokud potřebujete novou hodnotu v okamžiku kliknutí, jednou z možností je vypočítat, co očekávaná hodnota bude založena na aktuální hodnotě. Dalším přístupem je okamžité potvrzení změny a zpracování události <xref:System.Windows.Forms.DataGridView.CellValueChanged>, která na ni reaguje. Chcete-li změnu potvrdit při kliknutí na buňku, je nutné zpracovat událost <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>. Pokud je aktuální buňka v obslužné rutině buňka zaškrtávací políčko, zavolejte metodu <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> a předejte hodnotu <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> slouží k zobrazení obrázků. Sloupce obrázku mohou být naplněny automaticky ze zdroje dat, vyplněné pro nevázané sloupce nebo dynamicky naplněny v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 Automatické naplnění sloupce obrázku ze zdroje dat funguje s poli bajtů v nejrůznějších formátech obrázků, včetně všech formátů podporovaných <xref:System.Drawing.Image> třídou a formátu obrázků OLE, který používá Microsoft® Access a ukázkové databáze Northwind.  
  
 Ruční naplnění sloupce obrázku je užitečné, pokud chcete poskytnout funkce <xref:System.Windows.Forms.DataGridViewButtonColumn>, ale s přizpůsobeným vzhledem. Událost <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> můžete zpracovat tak, aby reagovala na kliknutí v rámci buňky obrázku.  
  
 Naplnění buněk sloupce obrázku v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting> je užitečné, pokud chcete poskytnout obrázky pro počítané hodnoty nebo hodnoty v neobrazovém formátu. Například můžete mít sloupec "rizik" s řetězcovými hodnotami, například `"high"`, `"middle"`a `"low"`, které chcete zobrazit jako ikony. Alternativně můžete mít sloupec "image", který obsahuje umístění obrázků, která musí být načtena místo binárního obsahu imagí.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewButtonColumn>můžete zobrazit sloupec buněk obsahující tlačítka. To je užitečné, když chcete uživatelům poskytnout snadný způsob, jak provádět akce s konkrétními záznamy, jako je například umístění objednávky nebo zobrazení podřízených záznamů v samostatném okně.  
  
 Sloupce tlačítek nejsou generovány automaticky při datové vazbě ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Chcete-li použít sloupce tlačítek, je nutné je vytvořit ručně a přidat je do kolekce vrácené vlastností <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>.  
  
 Můžete reagovat na kliknutí uživatele v buňkách tlačítek, a to zpracováním události <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewComboBoxColumn>můžete zobrazit sloupec buněk, které obsahují rozevírací seznamy. To je užitečné pro zadávání dat v polích, která mohou obsahovat pouze konkrétní hodnoty, jako je například sloupec kategorie v tabulce Products v ukázkové databázi Northwind.  
  
 Rozevírací seznam, který se používá pro všechny buňky, můžete naplnit stejným způsobem jako rozevírací seznam <xref:System.Windows.Forms.ComboBox>, a to buď ručně prostřednictvím kolekce vrácené vlastností <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>, nebo tak, že ji navážete na zdroj dat prostřednictvím vlastností <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. Další informace naleznete v tématu [ovládací prvek ComboBox](combobox-control-windows-forms.md).  
  
 Skutečné hodnoty buněk lze navazovat na zdroj dat používaný ovládacím prvkem <xref:System.Windows.Forms.DataGridView> nastavením vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Sloupce pole se seznamem nejsou generovány automaticky při vytváření datových vazeb ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Chcete-li použít sloupce pole se seznamem, je nutné je vytvořit ručně a přidat je do kolekce vrácené vlastností <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Pomocí <xref:System.Windows.Forms.DataGridViewLinkColumn>můžete zobrazit sloupec buněk obsahující hypertextové odkazy. To je užitečné pro hodnoty URL ve zdroji dat nebo jako alternativu k sloupci tlačítko pro zvláštní chování, jako je například otevření okna s podřízenými záznamy.  
  
 Sloupce odkazů nejsou generovány automaticky při vytváření datových vazeb ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Chcete-li použít sloupce odkazů, je nutné je vytvořit ručně a přidat je do kolekce vrácené vlastností <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
 Můžete reagovat na kliknutí na odkazy, které se zpracovávají <xref:System.Windows.Forms.DataGridView.CellContentClick> události. Tato událost se liší od událostí <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellMouseClick>, ke kterým dochází, když uživatel klikne kamkoli v buňce.  
  
 Třída <xref:System.Windows.Forms.DataGridViewLinkColumn> poskytuje několik vlastností pro úpravu vzhledu odkazů před, během a po kliknutí.  
  
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
