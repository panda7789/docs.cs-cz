---
title: Možnosti změny velikosti v ovládacím prvku DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769798"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Možnosti změny velikosti v ovládacím prvku DataGrid
Různé možnosti jsou k dispozici pro ovládací prvek jak <xref:System.Windows.Controls.DataGrid> velikosti samotného. <xref:System.Windows.Controls.DataGrid>a jednotlivých řádků a sloupců v <xref:System.Windows.Controls.DataGrid>, můžete nastavit pro nastavení velikosti automaticky jejich obsah, nebo můžete nastavit na konkrétní hodnoty. Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> bude zvětšovat a zmenšovat podle velikosti jeho obsah.  
  
## <a name="sizing-the-datagrid"></a>Velikost prvku DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Upozornění při použití automatické velikosti  
 Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti <xref:System.Windows.Controls.DataGrid> jsou nastaveny na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" v XAML) a <xref:System.Windows.Controls.DataGrid> přizpůsobí velikosti jeho obsah.  
  
 Při umístění uvnitř kontejneru, který vás neomezuje velikost jejích potomků, například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.DataGrid> roztáhnete nad rámec viditelné hranice kontejneru a posuvníky se nezobrazí. Tato podmínka má vliv na použitelnost a výkon.  
  
 Při vázání na datové sady, pokud <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> není omezený, bude nadále přidejte řádek pro každou položku dat v datové sadě vázaná. To může způsobit <xref:System.Windows.Controls.DataGrid> růst s mimo viditelné hranice vaší aplikace se přidají řádky. <xref:System.Windows.Controls.DataGrid> Nebudou zobrazovat posuvníky v tomto případě protože jeho <xref:System.Windows.FrameworkElement.Height%2A> budou i nadále odpovídajícím způsobem zvětší nových řádků.  
  
 Vytvoří objekt pro každý řádek <xref:System.Windows.Controls.DataGrid>. Pokud pracujete s velkých sadách dat a chcete povolit <xref:System.Windows.Controls.DataGrid> k automaticky přizpůsobovat svou velikost, může vytvářet velký počet objektů vliv na výkon vaší aplikace.  
  
 K těmto potížím vyhnout, když pracujete s velkými datovými sadami, je doporučeno, konkrétně nastavena <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Controls.DataGrid> nebo umístěte ho do kontejneru, který omezí jeho <xref:System.Windows.FrameworkElement.Height%2A>, například <xref:System.Windows.Controls.Grid>. Když <xref:System.Windows.FrameworkElement.Height%2A> je omezená, <xref:System.Windows.Controls.DataGrid> vytvoří pouze řádky, které se vejde jeho zadané <xref:System.Windows.FrameworkElement.Height%2A>a budou recyklovat řádky, podle potřeby zobrazit nová data.  
  
### <a name="setting-the-datagrid-size"></a>Nastavení velikosti ovládacího prvku DataGrid  
 <xref:System.Windows.Controls.DataGrid> Lze nastavit na automaticky velikost v rámci zadané hranice, nebo <xref:System.Windows.Controls.DataGrid> můžete nastavit na určité velikosti. V následující tabulce jsou uvedeny vlastnosti, které je možné nastavit na ovládací prvek <xref:System.Windows.Controls.DataGrid> velikost.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Nastaví konkrétní výšku <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Nastaví horní mez pro výšku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Poroste svisle, dokud nedosáhne tato výška.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Nastaví dolní mez pro výšku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Svisle zmenší, dokud nedosáhne tato výška.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Nastaví konkrétní šířku <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Nastaví horní mez pro šířku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Dokud nedosáhne tato šířka se horizontálně zvýší.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Nastaví dolní mez pro šířku <xref:System.Windows.Controls.DataGrid>. <xref:System.Windows.Controls.DataGrid> Vodorovně zmenší, dokud nedosáhne tuto šířku.|  
  
## <a name="sizing-rows-and-row-headers"></a>Nastavení velikosti řádků a záhlaví řádků  
  
### <a name="datagrid-rows"></a>Řádky ovládacího prvku DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> řádku <xref:System.Windows.FrameworkElement.Height%2A> je nastavena na <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" v XAML), a výšku řádku se rozbalí a velikosti jeho obsah. Výška všech řádků v <xref:System.Windows.Controls.DataGrid> se dá nastavit tak, že nastavíte <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> vlastnost. Uživatelé mohou změnit výšku řádku tažení oddělovače záhlaví řádku.  
  
### <a name="datagrid-row-headers"></a>Záhlaví řádků ovládacího prvku DataGrid  
 Chcete-li zobrazit záhlaví řádků <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být vlastnost nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Ve výchozím nastavení se zobrazí záhlaví řádků a automaticky velikost podle jejich obsahu. Záhlaví řádků je možné přidělit požadovanou šířku tak, že nastavíte <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> vlastnost.  
  
## <a name="sizing-columns-and-column-headers"></a>Změna velikosti sloupců a záhlaví sloupců  
  
### <a name="datagrid-columns"></a>DataGrid – sloupce  
 <xref:System.Windows.Controls.DataGrid> Používá hodnoty <xref:System.Windows.Controls.DataGridLength> a <xref:System.Windows.Controls.DataGridLengthUnitType> struktura určit režimů změny velikosti absolutní nebo automaticky.  
  
 V následující tabulce jsou uvedeny hodnoty poskytnuté <xref:System.Windows.Controls.DataGridLengthUnitType> struktury.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Automatická velikost velikosti režimu výchozí <xref:System.Windows.Controls.DataGrid> sloupce na základě obsahu buněk a záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Automaticky na základě buňky velikosti režim změny velikosti <xref:System.Windows.Controls.DataGrid> sloupce na základě obsahu buněk ve sloupci bez zahrnutí záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Automatické založeným na hlavičkách velikosti režim změny velikosti <xref:System.Windows.Controls.DataGrid> sloupce na základě obsahu pouze záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Pixel podle velikosti režim změny velikosti <xref:System.Windows.Controls.DataGrid> sloupce na základě číselné hodnoty k dispozici.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Režim změny velikosti hvězdičky se používá k distribuci dostupné místo podle vážený rozměry.<br /><br /> V XAML hvězdičky hodnoty jsou vyjádřeny jako n * kde n reprezentuje číselnou hodnotu. 1\* je ekvivalentní \*. Například, pokud dva sloupce v <xref:System.Windows.Controls.DataGrid> měl šířku \* . a 2\*, obdrží jednu část dostupného místa na první sloupec a druhý sloupec obdrží dvě části volného místa.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> Třídy lze použít k převedení dat mezi číselné nebo řetězcové hodnoty a <xref:System.Windows.Controls.DataGridLength> hodnoty.  
  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>a <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Pokud je režim změny velikosti nastavená na <xref:System.Windows.Controls.DataGridLength.Auto%2A> nebo <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, sloupce se zvýší jejich nejširším viditelného obsahu podle šířky. Při posouvání, těchto režimů změny velikosti způsobí, že sloupce rozbalte Pokud obsahu, které je větší než aktuální velikost sloupce je přesunut do oblasti zobrazení. Sloupec nebude zmenšit po obsah možnosti posouvat určitý objekt mimo zobrazení.  
  
 Sloupce v <xref:System.Windows.Controls.DataGrid> můžete také nastavit na automaticky velikost pouze v určených hranicích, považují nebo sloupce může být nastavena na určité velikosti. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit k řízení velikosti sloupce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro jednotlivé sloupce. Přepíše <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Nastaví dolní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Nastaví dolní mez pro jednotlivé sloupce. Přepíše <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro všechny sloupce v <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro jednotlivé sloupce. Přepíše <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>Záhlaví sloupců ovládacího prvku DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> jsou zobrazena záhlaví sloupců. Skrytí záhlaví sloupců <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být vlastnost nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Ve výchozím nastavení když jsou zobrazena záhlaví sloupců, jsou automaticky velikost podle jejich obsahu. Záhlaví sloupců je možné přidělit určité výšky tak, že nastavíte <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Uživatelé mohou změnit výšku <xref:System.Windows.Controls.DataGrid> řádky a sloupce přetažením záhlaví oddělovačů řádků nebo sloupců. <xref:System.Windows.Controls.DataGrid> Také podporuje automatickou změnu velikosti řádků a sloupců dvojitým kliknutím na oddělovač záhlaví řádku nebo sloupce. Chcete-li zabránit Změna velikosti sloupců konkrétní uživatele, nastavte <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost `false` pro jednotlivé sloupce. Chcete-li uživatelům zabránit ve změně velikosti všechny sloupce, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost `false`. Chcete-li uživatelům zabránit ve změně velikosti všechny řádky, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> vlastnost `false`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
