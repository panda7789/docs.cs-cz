---
title: Výchozí chování klávesnice a myši v ovládacím prvku DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 6be464ce85bd3ba91dd6e6cc810ec7d04edc0c3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083319"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>Výchozí chování klávesnice a myši v ovládacím prvku DataGrid
Toto téma popisuje, jak mohou uživatelé komunikovat s <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí klávesnice a myši.  
  
 Typické interakce s <xref:System.Windows.Controls.DataGrid> zahrnují navigace, výběru a úpravy. Výběr chování má vliv <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> vlastnosti. Výchozí hodnoty, které způsobí, že chování popsané v tomto tématu jsou <xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType> a <xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>. Změny těchto hodnot může způsobit, že chování, které se liší od popsané. Když je buňka v režimu úprav, ovládací prvek pro úpravu může přepsat chování standardní klávesnice <xref:System.Windows.Controls.DataGrid>.  
  
## <a name="default-keyboard-behavior"></a>Výchozí chování klávesnice  
 V následující tabulce jsou uvedeny výchozí chování klávesnice <xref:System.Windows.Controls.DataGrid>.  
  
|Klávesy nebo kombinace kláves|Popis|  
|----------------------------|-----------------|  
|ŠIPKA DOLŮ|Přesune fokus na buňku přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, stisknutím šipky dolů nemá žádný účinek.|  
|ŠIPKA NAHORU|Přesune fokus na buňku přímo nad aktuální buňky. Pokud je zaměření na prvním řádku, stisknutím šipky nahoru nemá žádný účinek.|  
|ŠIPKA DOLEVA|Přesune fokus na předcházejí buňky v řádku. Pokud je zaměřena tak do první buňky v řádku, stisknutím klávesy šipka vlevo nemá žádný účinek.|  
|ŠIPKA DOPRAVA|Přesune fokus na další buňku v řádku. Pokud je zaměřena tak do poslední buňky v řádku, stisknutím klávesy šipka vpravo nemá žádný účinek.|  
|DOMOVSKÁ STRÁNKA|Přesune fokus na první buňky v aktuálním řádku.|  
|END|Přesune fokus na poslední buňku na aktuálním řádku.|  
|O STRÁNKU DOLŮ|Pokud nejsou seskupené řádky, posune ovládací prvek dolů podle počtu řádků, které jsou plně zobrazeny. Přesune fokus na poslední řádek plně zobrazené beze změny sloupců.<br /><br /> Pokud jsou seskupené řádky, přesune fokus na poslední řádek v <xref:System.Windows.Controls.DataGrid> beze změny sloupců.|  
|PAGE UP|Pokud nejsou seskupené řádky, posouvá směrem nahoru ovládacího prvku podle počtu řádků, které jsou plně zobrazeny. Přesune fokus na první řádek zobrazené beze změny sloupců.<br /><br /> Pokud jsou seskupené řádky, přesune fokus na první řádek <xref:System.Windows.Controls.DataGrid> beze změny sloupců.|  
|TAB|Přesune fokus na další buňku v aktuálním řádku. Pokud je zaměřena tak do poslední buňky v řádku, přesune fokus na první buňky v dalším řádku. Pokud je zaměřena tak do poslední buňky v ovládacím prvku, přesune fokus na další ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud aktuální buňka je v režimu úprav a stisknutím klávesy TAB způsobí, že se na přecházejí na aktuálním řádku, všechny změny, které byly provedeny na řádek usilujeme o to dříve, než se změní fokus.|  
|SHIFT+TAB|Přesune fokus na předchozí buňku na aktuálním řádku. Pokud je již zaměření první buňky řádku, přesune fokus na poslední buňky v předchozím řádku. Pokud je zaměřena tak do první buňky v ovládacím prvku, přesune fokus na předchozí ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud aktuální buňka je v režimu úprav a stisknutím klávesy TAB způsobí, že se na přecházejí na aktuálním řádku, všechny změny, které byly provedeny na řádek usilujeme o to dříve, než se změní fokus.|  
|CTRL + ŠIPKA DOLŮ|Přesune fokus na poslední buňky v aktuálním sloupci.|  
|CTRL + ŠIPKA NAHORU|Přesune fokus na první buňky v aktuálním sloupci.|  
|CTRL + ŠIPKA VPRAVO|Přesune fokus na poslední buňku na aktuálním řádku.|  
|CTRL + ŠIPKA DOLEVA|Přesune fokus na první buňky v aktuálním řádku.|  
|CTRL + HOME|Přesune fokus na první buňky v ovládacím prvku.|  
|CTRL+END|Přesune fokus na poslední buňky v ovládacím prvku.|  
|CTRL + PAGE DOWN|Odpovídá vlastnosti PAGE DOWN.|  
|CTRL + PAGE UP|Odpovídá vlastnosti PAGE UP.|  
|F2|Pokud <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType> vlastnost `false` a <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType> vlastnost `false` v aktuálním sloupci, vloží aktuální buňky do buňky režimu úprav.|  
|ZADEJTE|Potvrdí změny aktuální buňky a buňku a přesune fokus na buňku přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, potvrdí změny bez přesouvání fokus.|  
|ESC|Pokud je ovládací prvek v režimu úprav, zruší úpravy a vrátí se všechny změny, které byly provedeny v ovládacím prvku. Pokud z podkladového zdroje implementuje <xref:System.ComponentModel.IEditableObject>, stiskněte klávesu ESC podruhé zruší režimu úprav pro celý řádek.|  
|BACKSPACE|Odstraní znak za kurzorem při úpravách buňky.|  
|DELETE|Odstraní znak za kurzorem při úpravách buňky.|  
|CTRL+ENTER|Potvrzení změny bez přesouvání fokus na aktuální buňku.|  
|CTRL+A|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, vybere všechny řádky <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="selection-keys"></a>Výběr klíče  
 Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, chování navigace nezmění, ale navigaci pomocí klávesnice, při stisknutí klávesy SHIFT (včetně CTRL + SHIFT) slouží k úpravě výběru více řádky. Před zahájením navigační ovládací prvek na aktuálním řádku označí jako na řádek ukotvení. Při navigaci při stisknutí klávesy SHIFT výběr zahrnuje všechny řádky mezi ukotvení řádku a aktuálního řádku.  
  
 Následující klíče výběr změnit výběr více řádků.  
  
-   SHIFT + ŠIPKA DOLŮ  
  
-   SHIFT + ŠIPKA NAHORU  
  
-   SHIFT + PAGE DOWN  
  
-   SHIFT + PAGE UP  
  
-   CTRL + SHIFT + ŠIPKA DOLŮ  
  
-   CTRL + SHIFT + ŠIPKA NAHORU  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL+SHIFT+END  
  
## <a name="default-mouse-behavior"></a>Chování myši  
 V následující tabulce jsou uvedeny výchozí chování myši <xref:System.Windows.Controls.DataGrid>.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Klikněte na řádek nevybrané|Díky řádku kliknutí na aktuální řádek a kliknutí na buňku na aktuální buňku.|  
|Klikněte na aktuální buňku|Vloží aktuální buňka do režimu úprav.|  
|Přetáhněte buňky záhlaví sloupce|Pokud <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType> vlastnost `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType> vlastnost `true` v aktuálním sloupci, přesunete sloupec tak, aby ji můžete přetáhnout do nové pozice.|  
|Přetáhněte oddělovač záhlaví sloupců|Pokud <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> je vlastnost `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> vlastnost `true` aktuálního sloupce změní velikost sloupce.|  
|Dvakrát klikněte na oddělovač záhlaví sloupců|Pokud <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> vlastnost je `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> je vlastnost `true` v aktuálním sloupci, automatické velikosti sloupců pomocí <xref:System.Windows.Controls.DataGridLength.Auto%2A> Režim velikosti.|  
|Klikněte na buňky záhlaví sloupce|Pokud <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType> vlastnost `true` a <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType> vlastnost `true` aktuálního sloupce seřadí sloupec.<br /><br /> Směr řazení sloupce vrátíte zpět kliknutím na záhlaví sloupce, který už není seřazen.<br /><br /> Stisknutím klávesy SHIFT při kliknutím na více záhlaví sloupce seřadíte více sloupců v pořadí, kliknutí na.|  
|CTRL + kliknutím na řádek|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, upraví nesouvislé výběr více řádků.<br /><br /> Pokud řádek je zaškrtnuto, zrušit výběr řádku.|  
|SHIFT + kliknutí myši řádek|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, upraví souvislý výběr více řádků.|  
|Klikněte na záhlaví skupiny řádků|Rozbalí nebo sbalí skupinu.|  
|Klikněte na tlačítko Vybrat vše v levém horním rohu <xref:System.Windows.Controls.DataGrid>|Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, vybere všechny řádky <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="mouse-selection"></a>Výběr myši  
 Pokud <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> je nastavena na <xref:System.Windows.Controls.DataGridSelectionMode.Extended>, kliknutím na řádek při stisknutí klávesy CTRL nebo SHIFT slouží k úpravě výběru více řádky.  
  
 Po kliknutí na řádek při stisknutí klávesy CTRL, řádku se změní jeho stav výběru, zatímco všechny ostatní řádky se zachovat jejich aktuální stav výběru. Proveďte to k výběru nesousedících řádky.  
  
 Po kliknutí na řádek při stisknutí klávesy SHIFT, výběr zahrnuje všechny řádky mezi aktuální řádek a na ukotvení řádek na pozici před kliknutím na aktuálním řádku. Následné kliknutí při stisknutí klávesy SHIFT změnit aktuální řádek, ale ne ukotvení řádku. Vybrat rozsah řádků sousední to proveďte.  
  
 CTRL + SHIFT zkombinovat k výběru nesousedících rozsahy sousední řádků. Chcete-li to provést, vyberte v první oblasti pomocí klávesy SHIFT + klikněte na možnost, jak je popsáno výše. Po výběru prvního rozsah řádků pomocí kláves CTRL + kliknutím vyberte první řádek v další oblasti a pak klikněte na poslední řádek v další oblasti při stisknutí klávesy CTRL + SHIFT.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
