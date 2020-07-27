---
title: Možnosti změny velikosti v ovládacím prvku DataGrid
description: Naučte se, jak nastavit jednotlivé řádky a sloupce v Windows Presentation Foundation ovládacím prvku DataGrid na velikost jejich obsahu nebo na konkrétní hodnoty.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164744"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Možnosti změny velikosti v ovládacím prvku DataGrid
K dispozici jsou různé možnosti, které určují, jak <xref:System.Windows.Controls.DataGrid> samotné velikosti. <xref:System.Windows.Controls.DataGrid>A jednotlivé řádky a sloupce v <xref:System.Windows.Controls.DataGrid> lze nastavit tak, aby se automaticky změnily na jejich obsah nebo mohly být nastaveny na konkrétní hodnoty. Ve výchozím nastavení se zvětší <xref:System.Windows.Controls.DataGrid> a zmenší tak, aby odpovídala velikosti jejího obsahu.  
  
## <a name="sizing-the-datagrid"></a>Změna velikosti ovládacího prvku DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Upozornění při použití automatického určení velikosti  
 Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti a <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DataGrid> jsou nastaveny na <xref:System.Double.NaN?displayProperty=nameWithType> (" `Auto` " v jazyce XAML) a se <xref:System.Windows.Controls.DataGrid> přizpůsobí velikosti jejího obsahu.  
  
 Při umístění do kontejneru, který neomezuje velikost jeho podřízených prvků, jako je například <xref:System.Windows.Controls.Canvas> nebo <xref:System.Windows.Controls.StackPanel> , se <xref:System.Windows.Controls.DataGrid> roztáhne za viditelné hranice kontejneru a posuvníky nebudou zobrazeny. Tato podmínka má dopad na použitelnost i na výkon.  
  
 Pokud je objekt, který je svázán s datovou sadou, v případě, že není <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> omezen, bude pokračovat přidáním řádku pro každou datovou položku v vázané datové sadě. To může způsobit, že se při <xref:System.Windows.Controls.DataGrid> Přidání řádků z aplikace rozroste mimo viditelné hranice vaší aplikace. <xref:System.Windows.Controls.DataGrid>V tomto případě nebudou v tomto případě zobrazeny posuvníky, protože <xref:System.Windows.FrameworkElement.Height%2A> se bude nadále zvětšovat tak, aby se vešly na nové řádky.  
  
 Vytvoří se objekt pro každý řádek v <xref:System.Windows.Controls.DataGrid> . Pokud pracujete s velkou datovou sadou a povolíte <xref:System.Windows.Controls.DataGrid> automatickou vlastní velikost, vytvoření velkého počtu objektů může ovlivnit výkon aplikace.  
  
 Chcete-li se těmto problémům vyhnout při práci s velkými datovými sadami, doporučujeme, abyste konkrétně nastavili <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> nebo umístili ji do kontejneru, který omezí jeho <xref:System.Windows.FrameworkElement.Height%2A> , jako je třeba <xref:System.Windows.Controls.Grid> . Když <xref:System.Windows.FrameworkElement.Height%2A> je omezení omezené, <xref:System.Windows.Controls.DataGrid> vytvoří pouze řádky, které se vejdou do zadaného umístění <xref:System.Windows.FrameworkElement.Height%2A> , a bude tyto řádky recyklovat podle potřeby pro zobrazení nových dat.  
  
### <a name="setting-the-datagrid-size"></a>Nastavení velikosti objektu DataGrid  
 <xref:System.Windows.Controls.DataGrid>Lze nastavit na automatickou velikost v rámci zadaných hranic nebo <xref:System.Windows.Controls.DataGrid> lze nastavit na konkrétní velikost. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pro řízení <xref:System.Windows.Controls.DataGrid> velikosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Nastaví specifickou výšku pro <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Nastaví horní mez pro výšku <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Bude růst svisle, dokud nedosáhne této výšky.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Nastaví dolní mez pro výšku <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Zmenší se svisle, dokud nedosáhne této výšky.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Nastaví konkrétní šířku pro <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Nastaví horní mez pro šířku <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Dojde k vodorovnému zvětšení, dokud nedosáhne této šířky.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Nastaví dolní mez pro šířku <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Dojde k horizontálnímu zmenšení, dokud nedosáhne této šířky.|  
  
## <a name="sizing-rows-and-row-headers"></a>Změna velikosti řádků a záhlaví řádků  
  
### <a name="datagrid-rows"></a>Řádky DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.FrameworkElement.Height%2A> je vlastnost řádku nastavena na (" <xref:System.Double.NaN?displayProperty=nameWithType> `Auto` " v jazyce XAML) a výška řádku se rozšíří na velikost jejího obsahu. Výšku všech řádků v poli <xref:System.Windows.Controls.DataGrid> lze zadat nastavením <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> Vlastnosti. Uživatelé mohou změnit výšku řádku přetažením oddělovačů záhlaví řádků.  
  
### <a name="datagrid-row-headers"></a>Záhlaví řádků mřížky  
 Chcete-li zobrazit záhlaví řádků, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být vlastnost nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> . Ve výchozím nastavení se zobrazují záhlaví řádků a automaticky se přizpůsobí velikosti jejich obsahu. Záhlaví řádků lze určit specifickou šířku nastavením <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> Vlastnosti.  
  
## <a name="sizing-columns-and-column-headers"></a>Změna velikosti sloupců a záhlaví sloupců  
  
### <a name="datagrid-columns"></a>Sloupce DataGrid  
 <xref:System.Windows.Controls.DataGrid>Používá hodnoty <xref:System.Windows.Controls.DataGridLength> a <xref:System.Windows.Controls.DataGridLengthUnitType> struktury k určení absolutních nebo automatických nastavení velikosti.  
  
 V následující tabulce jsou uvedeny hodnoty poskytované <xref:System.Windows.Controls.DataGridLengthUnitType> strukturou.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Výchozí režim automatické velikosti určuje velikost <xref:System.Windows.Controls.DataGrid> sloupců na základě obsahu buněk a záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Režim automatické velikosti založený na buňkách <xref:System.Windows.Controls.DataGrid> mění velikost sloupců na základě obsahu buněk ve sloupci bez záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Režim automatického navýšení velikosti na základě záhlaví bude mít velikost <xref:System.Windows.Controls.DataGrid> sloupců na základě obsahu záhlaví sloupců.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Režim velikosti v pixelech přizpůsobí <xref:System.Windows.Controls.DataGrid> sloupce na základě zadané číselné hodnoty.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Režim změny velikosti hvězdičky se používá k distribuci dostupného místa podle váženého poměru.<br /><br /> V jazyce XAML se hodnoty hvězdiček vyjadřují jako n *, kde n představuje číselnou hodnotu. 1 \* je ekvivalentem k \* . Pokud například dva sloupce v <xref:System.Windows.Controls.DataGrid> mají šířku \* a 2 \* , první sloupec obdrží jednu část dostupného místa a druhý sloupec by dostal dvě části dostupného místa.|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>Třída se dá použít k převodu dat mezi číselnými nebo řetězcovými hodnotami a <xref:System.Windows.Controls.DataGridLength> hodnotami.  
  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> je vlastnost nastavena na hodnotu <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> a <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> vlastnost je nastavena na hodnotu <xref:System.Windows.Controls.DataGridLength.Auto%2A> . Když je režim změny velikosti nastavený na <xref:System.Windows.Controls.DataGridLength.Auto%2A> nebo <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> , sloupce se zvětší na šířku jejich nejširšího viditelného obsahu. Při posouvání budou tyto režimy změny velikosti způsobit, že se sloupce rozbalí, pokud se obsah, který je větší než aktuální velikost sloupce, posune do zobrazení. Sloupec se nezmenší po posunutí obsahu mimo zobrazení.  
  
 Sloupce v <xref:System.Windows.Controls.DataGrid> lze také nastavit tak, aby automaticky změnily velikost pouze v zadaných hranicích, nebo je možné nastavit sloupce na konkrétní velikost. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pro řízení velikostí sloupců.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Nastaví horní mez pro jednotlivý sloupec. Přepisuje <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Nastaví dolní mez pro všechny sloupce v <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Nastaví dolní mez pro jednotlivý sloupec. Přepisuje <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType> .|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro všechny sloupce v <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Nastaví konkrétní šířku pro jednotlivý sloupec. Přepisuje <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> .|  
  
### <a name="datagrid-column-headers"></a>Záhlaví sloupců DataGrid  
 Ve výchozím nastavení <xref:System.Windows.Controls.DataGrid> se zobrazují záhlaví sloupců. Chcete-li skrýt záhlaví sloupců, <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> musí být vlastnost nastavena na <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> nebo <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> . Ve výchozím nastavení se při zobrazení záhlaví sloupců automaticky přizpůsobí velikosti podle jejich obsahu. Záhlaví sloupců lze určit specifickou výškou nastavením <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> Vlastnosti.  
  
### <a name="resizing-with-the-mouse"></a>Změna velikosti pomocí myši  
 Uživatelé mohou změnit velikost <xref:System.Windows.Controls.DataGrid> řádků a sloupců přetažením oddělovačů záhlaví řádků nebo sloupců. <xref:System.Windows.Controls.DataGrid>Podporuje také automatické změny velikosti řádků a sloupců dvojitým kliknutím na oddělovač záhlaví řádku nebo sloupce. Chcete-li uživateli zabránit v změně velikosti určitých sloupců, nastavte <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost na hodnotu `false` pro jednotlivé sloupce. Chcete-li uživatelům zabránit ve změně velikosti všech sloupců, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost na hodnotu `false` . Chcete-li uživatelům zabránit ve změně velikosti všech řádků, nastavte <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> vlastnost na hodnotu `false` .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
