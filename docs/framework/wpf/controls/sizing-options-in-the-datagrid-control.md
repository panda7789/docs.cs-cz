---
title: Možnosti změny velikosti v ovládacím prvku DataGrid
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4219dc88a263b73aa89812a2f841a920c804796b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="sizing-options-in-the-datagrid-control"></a>Možnosti změny velikosti v ovládacím prvku DataGrid
Různé možnosti jsou k dispozici pro ovládací prvek jak <xref:System.Windows.Controls.DataGrid> velikosti sám sebe. <xref:System.Windows.Controls.DataGrid>a jednotlivých řádků a sloupců v <xref:System.Windows.Controls.DataGrid>, může být nastaven na automaticky velikost na jejich obsah, nebo můžete nastavit na konkrétní hodnoty. Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> bude zvýšit nebo snížit přizpůsobit velikost jeho obsahu.  
  
## <a name="sizing-the-datagrid"></a>Změna velikosti v kolekci DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Upozornění při použití Automatická změna velikosti  
 Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti <xref:System.Windows.Controls.DataGrid> jsou nastaveny na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" v jazyce XAML) a <xref:System.Windows.Controls.DataGrid> upraví velikost jeho obsah.  
  
 Když umístěn uvnitř kontejner, který neomezuje velikost své podřízené objekty, například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> se roztáhnou za viditelné hranice kontejneru a nebude se zobrazovat posuvníky. Tato podmínka má důsledky, použitelnost a výkon.  
  
 Při vázání na datové sady, pokud <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> není omezený, bude pokračovat řádek pro každou položku dat přidat do vázané datové sady. To může způsobit <xref:System.Windows.Controls.DataGrid> růst mimo viditelné hranice vaší aplikace s jsou přidány řádky. <xref:System.Windows.Controls.DataGrid> Posuvníky v tomto případě proto nezobrazí jeho <xref:System.Windows.FrameworkElement.Height%2A> pořád roste s tím zohlednit nové řádky.  
  
 Vytvoření objektu pro každý řádek <xref:System.Windows.Controls.DataGrid>. Pokud pracujete s velké datové sady a povolíte <xref:System.Windows.Controls.DataGrid> automaticky velikost sám, může vytvářet velký počet objektů vliv na výkon vaší aplikace.  
  
 Nechcete tyto problémy při práci s velkých datových sad, se doporučuje, aby výslovně nastavit <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> nebo umístit ho do kontejneru, který se omezí jeho <xref:System.Windows.FrameworkElement.Height%2A>, například <xref:System.Windows.Controls.Grid>. Když <xref:System.Windows.FrameworkElement.Height%2A> je omezená, <xref:System.Windows.Controls.DataGrid> vytvoří pouze řádky, na které se vejde do jeho zadaný <xref:System.Windows.FrameworkElement.Height%2A>a bude recyklovat tyto řádky, podle potřeby zobrazíte nová data.  
  
### <a name="setting-the-datagrid-size"></a>Nastavení velikosti ovládacího prvku DataGrid  
 <xref:System.Windows.Controls.DataGrid> Může být nastaven na automaticky velikost v rámci určených hranicích, nebo <xref:System.Windows.Controls.DataGrid> lze nastavit na konkrétní velikost. V následující tabulce jsou uvedeny vlastnosti, které může být nastaven na ovládací prvek <xref:System.Windows.Controls.DataGrid> velikost.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Nastaví pro určité výšky <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Nastaví horní mez pro výšku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Poroste ve svislém směru, dokud nebude dosaženo této výšku.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Nastaví dolní mez pro výšku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Svisle zmenší, dokud nebude dosaženo této výšku.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Nastaví konkrétní šířku pro <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Nastaví horní mez pro šířku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Poroste vodorovně, dokud nebude dosaženo tuto šířku.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Nastaví dolní mez pro šířku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Vodorovně zmenší, dokud nebude dosaženo tuto šířku.|  
  
## <a name="sizing-rows-and-row-headers"></a>Nastavení velikosti řádků a záhlaví řádků  
  
### <a name="datagrid-rows"></a>Řádky DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> řádku <xref:System.Windows.FrameworkElement.Height%2A> je nastavena na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" v jazyce XAML), a výšku řádku se rozbalí a velikost jeho obsahu. Výška všechny řádky v <xref:System.Windows.Controls.DataGrid> lze zadat nastavením <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> vlastnost. Uživatelé můžou změnit výška řádku přetažením oddělovačů řádek záhlaví.  
  
### <a name="datagrid-row-headers"></a>Záhlaví řádků DataGrid  
 Chcete-li zobrazit záhlaví řádků <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Ve výchozím nastavení se zobrazí záhlaví řádků a jejich velikost automaticky podle jejich obsahu. Záhlaví řádků je možné přidělit požadovanou šířku nastavením <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="sizing-columns-and-column-headers"></a>Změna velikosti sloupců a záhlaví sloupců  
  
### <a name="datagrid-columns"></a>Sloupců DataGrid  
 <xref:System.Windows.Controls.DataGrid> Používá hodnoty <xref:System.Windows.Controls.DataGridLength> a <xref:System.Windows.Controls.DataGridLengthUnitType> struktura určující režimů změny velikosti absolutní nebo automaticky.  
  
 Následující tabulka zobrazuje hodnoty poskytované <xref:System.Windows.Controls.DataGridLengthUnitType> struktura.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Automatická změna velikosti režimu velikosti výchozí <xref:System.Windows.Controls.DataGrid> sloupců na základě obsahu buněk a záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Na základě buňky Automatická změna velikosti režimu velikosti <xref:System.Windows.Controls.DataGrid> sloupců na základě obsahu buněk ve sloupci není včetně záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Na základě záhlaví Automatická změna velikosti režimu velikosti <xref:System.Windows.Controls.DataGrid> sloupců na základě obsahu pouze záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Základě pixelů dimenzování režimu velikosti <xref:System.Windows.Controls.DataGrid> sloupců založené na číselnou hodnotu zadat.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Režim hvězdičkami velikosti slouží k distribuci dostupné místo vyvážené proporce.<br /><br /> Hvězdičky. hodnoty jsou v jazyce XAML, vyjádřené jako n * kde n reprezentuje číselnou hodnotu. 1\* je ekvivalentní \*. Například, pokud dva sloupce v <xref:System.Windows.Controls.DataGrid> měl šířku \* a 2\*, první sloupec by přijímat jednu část prostoru a druhý sloupec obdrží dvě části dostupného místa.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Třídu lze použít k převodu dat mezi hodnotami číselnou nebo řetězec a <xref:System.Windows.Controls.DataGridLength> hodnoty.  
  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>a <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Když je režim velikosti nastavená na <xref:System.Windows.Controls.DataGridLength.Auto%2A> nebo <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, sloupce se zvýší na šířku jejich co nejširším měřítku viditelný obsah. Při posouvání, tyto režimy změny velikosti způsobí, že sloupců Pokud obsahu, které je větší než aktuální velikost sloupce je přesunut do zobrazení oblasti. Sloupec nebude zmenšit po obsah přesunut oblasti mimo zobrazení.  
  
 Sloupce v <xref:System.Windows.Controls.DataGrid> lze také nastavit automaticky velikost pouze v určených hranicích, nebo sloupce může být nastavena na konkrétní velikost. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pro řízení velikosti sloupce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro jednotlivé sloupce. Přepsání <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Nastaví dolní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Nastaví dolní hranice pro jednotlivé sloupce. Přepsání <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro jednotlivé sloupce. Přepsání <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>Záhlaví sloupců DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> záhlaví sloupců jsou zobrazeny. Skrytí záhlaví sloupců <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Ve výchozím nastavení Jakmile se zobrazí záhlaví sloupců, budou automaticky velikost podle jejich obsahu. Záhlaví sloupců může být poskytnut určité výšky nastavením <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Uživatelé mohou změnit <xref:System.Windows.Controls.DataGrid> řádků a sloupců přetažením oddělovačů záhlaví sloupce či řádku. <xref:System.Windows.Controls.DataGrid> Také podporuje Automatická změna velikosti řádků a sloupců dvojitým kliknutím na soubor oddělovač záhlaví sloupce či řádku. Chcete-li zabránit Změna velikosti sloupců konkrétní uživatele, nastavte <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost `false` pro jednotlivé sloupce. Chcete-li zabránit uživatelům v Změna velikosti všechny sloupce, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost `false`. Chcete-li zabránit uživatelům v Změna velikosti všechny řádky, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> vlastnost `false`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>
