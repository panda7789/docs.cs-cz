---
title: Výchozí chování klávesnice a myši v ovládacím prvku DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 559b84d3e6b5ece6c71f17e6766cac4ec14824cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Výchozí chování klávesnice a myši v ovládacím prvku DataGrid
Toto téma popisuje, jak mohou uživatelé komunikovat s <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí klávesnice a myši.  
  
 Typické interakce s <xref:System.Windows.Controls.DataGrid> zahrnují navigace, výběru a úpravy. Chování výběru mají vliv <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> vlastnosti. Výchozí hodnoty, které způsobují chování popsané v tomto tématu jsou <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> a <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Změna těchto hodnot může způsobit chování, které se liší od popsané. Když buňku je v režimu úprav, ovládacího prvku úprav může přepsat chování standardní klávesnice <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Výchozí chování klávesnice  
 Následující tabulka uvádí výchozí chování klávesnice <xref:System.Windows.Controls.DataGrid>.  
  
|Klíč nebo kombinaci kláves|Popis|  
|----------------------------|-----------------|  
|ŠIPKA DOLŮ|Přejdete k buňky přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, klávesy Šipka dolů neprovede žádnou akci.|  
|ŠIPKA NAHORU|Přejdete k buňky přímo nad aktuální buňky. Pokud je zaměření na prvním řádku, klávesy šipka nahoru neprovede žádnou akci.|  
|ŠIPKA DOLEVA|Přejdete k předchozí buňky v řádku. Pokud je zaměření v první buňky v řádku, klávesy šipka doleva neprovede žádnou akci.|  
|ŠIPKA DOPRAVA|Přejdete k dalším buňky v řádku. Pokud je zaměření v poslední buňky v řádku, kliknutím na šipku vpravo neprovede žádnou akci.|  
|DOMOVSKÉ|Přejdete k první buňky na aktuálním řádku.|  
|END|Přejdete na poslední buňku na aktuálním řádku.|  
|PAGE DOWN|Pokud nejsou seskupení řádků, posune ovládací prvek dolů podle počtu řádků, které jsou plně zobrazené. Změní na aktivní poslední řádek plně zobrazených beze změny sloupců.<br /><br /> Pokud jsou seskupeny řádky, přejdete k posledním řádkem <xref:System.Windows.Controls.DataGrid> beze změny sloupců.|  
|PAGE UP|Pokud nejsou seskupení řádků, posune nahoru ovládacího prvku podle počtu řádků, které jsou plně zobrazené. Přesun zaměření na první řádek zobrazených beze změny sloupců.<br /><br /> Pokud jsou seskupeny řádky, přejdete k první řádek v <xref:System.Windows.Controls.DataGrid> beze změny sloupců.|  
|KARTA|Přejdete k dalším buňky na aktuálním řádku. Pokud je zaměření v poslední buňky řádku, přejdete k první buňky v dalším řádku. Pokud je zaměření v poslední buňky v ovládacím prvku, přejdete na další ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud aktuální buňky v režimu úprav a kliknutím na kartu příčiny fokus přesunout mimo aktuální řádek, veškeré změny, které byly provedeny na řádek potvrzeny předtím, než se změní fokus.|  
|SHIFT + TAB|Přejdete k předchozí buňku na aktuálním řádku. Pokud je zaměření již první buňky řádku, přejdete k poslední buňky v předchozím řádku. Pokud je zaměření v první buňky v ovládacím prvku, přejdete k předchozí ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud aktuální buňky v režimu úprav a kliknutím na kartu příčiny fokus přesunout mimo aktuální řádek, veškeré změny, které byly provedeny na řádek potvrzeny předtím, než se změní fokus.|  
|CTRL + ŠIPKA DOLŮ|Přejdete na poslední buňku ve sloupci aktuální.|  
|CTRL + ŠIPKA NAHORU|Přejdete k první buňky v aktuální sloupec.|  
|CTRL + ŠIPKA VPRAVO|Přejdete na poslední buňku na aktuálním řádku.|  
|CTRL + ŠIPKA DOLEVA|Přejdete k první buňky na aktuálním řádku.|  
|CTRL + HOME|Přejdete k první buňky v ovládacím prvku.|  
|CTRL + END|Přejdete k poslední buňky v ovládacím prvku.|  
|CTRL + PAGE DOWN|Stejné jako PAGE DOWN.|  
|CTRL + PAGEUP|Stejné jako PageUp.|  
|F2|Pokud <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> vlastnost je `false` a <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> vlastnost je `false` pro aktuální sloupec vloží aktuální buňky do buňky režimu úprav.|  
|ZADEJTE|Potvrdí změny aktuální buňky a buňku a přejdete k buňky přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, potvrdí změny bez přesouvání fokus.|  
|ESC|Pokud ovládací prvek je v režimu úprav, zruší úpravy a obnoví všechny změny, které byly provedeny v ovládacím prvku. Pokud základní datové zdroje implementuje <xref:System.ComponentModel.IEditableObject>, dalším stisknutím ESC zruší režimu úprav pro celý řádek.|  
|BACKSPACE|Při úpravě buňku k odstranění znaku před kurzor.|  
|DELETE|Při úpravě buňku k odstranění znaku po kurzor.|  
|CTRL + ENTER|Neprovede žádné změny aktuální buňky bez přesouvání fokus.|  
|CTRL + A|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastaven na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, vybere všechny řádky <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Výběr klíče  
 Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, nezmění chování navigace, ale navigaci pomocí klávesnice, při stisknutí klávesy SHIFT (včetně CTRL + SHIFT) slouží k úpravě výběru více řádků. Před zahájením navigace, označí ovládacího prvku na aktuálním řádku jako řádek na ukotvení. Když přejdete při stisknutí klávesy SHIFT, výběr zahrnuje všechny řádky mezi řádek ukotvení a na aktuálním řádku.  
  
 Následující klíče výběr změnit výběr více řádků.  
  
-   SHIFT + ŠIPKA DOLŮ  
  
-   SHIFT + ŠIPKA NAHORU  
  
-   SHIFT + PAGE DOWN  
  
-   SHIFT + PAGEUP  
  
-   CTRL + SHIFT + ŠIPKA DOLŮ  
  
-   CTRL + SHIFT + ŠIPKA NAHORU  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL + SHIFT + END  
  
## <a name="default-mouse-behavior"></a>Výchozí chování myši  
 Následující tabulka uvádí výchozí chování myši <xref:System.Windows.Controls.DataGrid>.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Klikněte na tlačítko nezaškrtnuté řádek|Díky kliknutelnou řádek, na aktuálním řádku a buňky kliknutelnou aktuální buňky.|  
|Klikněte na aktuální buňky|Aktuální buňky umístí do režimu úprav.|  
|Přetáhněte datovou buňku sloupce|Pokud <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> vlastnost je `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> vlastnost je `true` pro aktuální sloupec přesune sloupce, takže může být přetažen do nového umístění.|  
|Přetáhněte oddělovače záhlaví sloupců|Pokud <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost je `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost je `true` pro aktuální sloupec změní sloupce.|  
|Klikněte dvakrát na oddělovače záhlaví sloupců|Pokud <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost je `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost je `true` pro aktuální sloupec automaticky velikosti sloupce pomocí <xref:System.Windows.Controls.DataGridLength.Auto%2A> nastavení velikosti režimu.|  
|Klikněte na buňku záhlaví sloupců|Pokud <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> vlastnost je `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> vlastnost je `true` aktuální sloupce seřadí sloupci.<br /><br /> Kliknutím na záhlaví sloupce, který je už seřazený bude obrátit směr řazení tohoto sloupce.<br /><br /> Podržíte klávesu SHIFT a kliknete na více záhlaví sloupce seřadíte více sloupců v pořadí, kliknutí na.|  
|CTRL + klikněte na řádek|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastaven na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, upraví nesouvislých výběr více řádků.<br /><br /> Pokud je vybrána řádek, zruší výběr řádku.|  
|SHIFT + klikněte na řádek|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastaven na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, upraví souvislý výběr více řádků.|  
|Klikněte na řádek záhlaví skupiny|Rozbalí či sbalí skupiny.|  
|Klikněte na tlačítko Vybrat vše v levém horním rohu <xref:System.Windows.Controls.DataGrid>|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastaven na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, vybere všechny řádky <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Výběr myši  
 Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, klikněte řádek, při stisknutí klávesy CTRL nebo SHIFT slouží k úpravě výběru více řádků.  
  
 Po kliknutí na tlačítko řádku a stisknutím klávesy CTRL řádek změní stav výběru při všech ostatních řádků zachovat jejich aktuální stav výběru. K tomu k výběru nesousedících řádků.  
  
 Po kliknutí na tlačítko řádku a stisknutím klávesy SHIFT výběr zahrnuje všechny řádky na aktuálním řádku až anchor řádek na pozici na aktuálním řádku před kliknutím na možnost. Následující klepnutí při stisknutí klávesy SHIFT změnit na aktuálním řádku, ale ne řádek ukotvení. K tomu vybrat rozsah, sousedících řádků.  
  
 CTRL + SHIFT lze spojovat k výběru nesousedících rozsahy sousedících řádků. To pokud chcete udělat, vyberte v první oblasti s použitím SHIFT + klikněte na tlačítko jak bylo popsáno výše. Po výběru prvního rozsah řádků se použít kombinaci kláves CTRL + kliknutím vyberte první řádek další oblasti a pak na poslední řádek v další rozsahu při stisknutí klávesy CTRL + SHIFT.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
