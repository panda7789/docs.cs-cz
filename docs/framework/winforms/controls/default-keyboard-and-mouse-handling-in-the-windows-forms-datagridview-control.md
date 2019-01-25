---
title: Výchozí klávesnice a myši v ovládacím prvku Windows Forms DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 4d0a3cb7a56b388ee9bd3f932f9fec604b39fa62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521761"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Výchozí klávesnice a myši v ovládacím prvku Windows Forms DataGridView

Následující tabulky popisují, jak mohou uživatelé komunikovat s <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí klávesnice a myši.  
  
> [!NOTE]
>  Přizpůsobení chování klávesnice, můžete zpracovávat události standardní klávesnice, jako <xref:System.Windows.Forms.Control.KeyDown>. V režimu úprav, ale hostované ovládací prvek pro úpravu přijímá vstup z klávesnice a události klávesnice pro nedochází, <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Zpracování událostí úprav ovládacího prvku, připojit k ovládací prvek pro úpravu v obslužné rutině <xref:System.Windows.Forms.DataGridView.EditingControlShowing> obslužné rutiny události. Alternativně můžete přizpůsobit chování klávesnice <xref:System.Windows.Forms.DataGridView> podtřídy tak, že přepíšete <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> a <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> metody.  
  
## <a name="default-keyboard-handling"></a>Výchozí zpracování klávesnice  
  
### <a name="basic-navigation-and-entry-keys"></a>Základní navigace a položka klíče  
  
|Klávesy nebo kombinace kláves|Popis|  
|----------------------------|-----------------|  
|ŠIPKA DOLŮ|Přesune fokus na buňku přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, nemá žádný účinek.|  
|ŠIPKA DOLEVA|Přesune fokus na předcházejí buňky v řádku. Pokud je zaměřena tak do první buňky v řádku, nemá žádný účinek.|  
|ŠIPKA DOPRAVA|Přesune fokus na další buňku v řádku. Pokud je zaměřena tak do poslední buňky v řádku, nemá žádný účinek.|  
|ŠIPKA NAHORU|Přesune fokus na buňku přímo nad aktuální buňky. Pokud je zaměření na prvním řádku, nemá žádný účinek.|  
|DOMOVSKÁ STRÁNKA|Přesune fokus na první buňky v aktuálním řádku.|  
|END|Přesune fokus na poslední buňku na aktuálním řádku.|  
|O STRÁNKU DOLŮ|Posune ovládací prvek dolů podle počtu řádků, které jsou plně zobrazeny. Přesune fokus na poslední řádek plně zobrazené beze změny sloupců.|  
|PAGE UP|Posune ovládací prvek směrem nahoru podle počtu řádků, které jsou plně zobrazeny. Přesune fokus na první řádek zobrazené beze změny sloupců.|  
|TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přesune fokus na další buňku v aktuálním řádku. Pokud už fokus do poslední buňky v řádku, přesune fokus na první buňky v dalším řádku. Pokud je zaměřena tak do poslední buňky v ovládacím prvku, přesune fokus na další ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přesune fokus na další ovládací prvek v pořadí jeho nadřazeného kontejneru.|  
|SHIFT+TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přesune fokus na předchozí buňku na aktuálním řádku. Pokud je již zaměření první buňky řádku, přesune fokus na poslední buňky v předchozím řádku. Pokud je zaměřena tak do první buňky v ovládacím prvku, přesune fokus na předchozí ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přesune fokus na předchozí ovládací prvek v pořadí jeho nadřazeného kontejneru.|  
|CTRL+TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přesune fokus na další ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přesune fokus na další buňku v aktuálním řádku. Pokud už fokus do poslední buňky v řádku, přesune fokus na první buňky v dalším řádku. Pokud je zaměřena tak do poslední buňky v ovládacím prvku, přesune fokus na další ovládací prvek v pořadí jeho nadřazeného kontejneru.|  
|CTRL+SHIFT+TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přesune fokus na předchozí ovládací prvek v pořadí jeho nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přesune fokus na předchozí buňku na aktuálním řádku. Pokud je již zaměření první buňky řádku, přesune fokus na poslední buňky v předchozím řádku. Pokud je zaměřena tak do první buňky v ovládacím prvku, přesune fokus na předchozí ovládací prvek v pořadí jeho nadřazeného kontejneru.|  
|CTRL + ŠIPKA|Přesune fokus na buňku nejvíce směrem šipky.|  
|CTRL + HOME|Přesune fokus na první buňky v ovládacím prvku.|  
|CTRL+END|Přesune fokus na poslední buňky v ovládacím prvku.|  
|CTRL + PAGE DOWN/NAHORU|Totéž jako PAGE DOWN nebo stránku nahoru.|  
|F2|Vloží aktuální buňky do buňky režimu úprav, pokud <xref:System.Windows.Forms.DataGridView.EditMode%2A> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> nebo <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Seřadí aktuální sloupec, pokud <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Je stejný jako při kliknutí na aktuální záhlaví sloupce. Dostupné od verze rozhraní .NET Framework 4.7.2. Pokud chcete tuto funkci povolit, aplikace musí cílit na rozhraní .NET Framework 4.7.2 nebo novější verze nebo explicitně přihlašují pomocí přepínačů AppContext vylepšení přístupnosti.|  
|F4|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umístí do režimu úprav buňku a zobrazí rozevírací seznam.|  
|ALT + ŠIPKA NAHORU/ŠIPKA|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umístí do režimu úprav buňku a zobrazí rozevírací seznam.|  
|MÍSTO|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, nebo <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, vyvolá <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellContentClick> události. Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewButtonCell>, také stiskne tlačítko. Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, také změní stav kontroly.|  
|ZADEJTE|Potvrdí změny aktuální buňky a buňku a přesune fokus na buňku přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, potvrdí změny bez přesouvání fokus.|  
|ESC|Pokud je ovládací prvek v režimu úprav, zruší upravit. Pokud ovládací prvek není v režimu úprav, vrátí se všechny změny, které byly provedeny na aktuálním řádku Pokud je ovládací prvek vázán na zdroj dat, který podporuje úpravy nebo implementoval virtuálního režimu s rozsahem potvrzení změn na úrovni řádků.|  
|BACKSPACE|Odstraní znak před kurzoru při úpravách buňky.|  
|DELETE|Odstraní znak za kurzorem při úpravách buňky.|  
|CTRL+ENTER|Potvrzení změny bez přesouvání fokus na aktuální buňku. Také všechny změny na aktuálním řádku, pokud je ovládací prvek vázán ke zdroji dat, který podporuje režim úprav nebo virtuální implementován s potvrzení změn na úrovni řádků rozsah potvrzení.|  
|CTRL+0|Zadá <xref:System.DBNull.Value?displayProperty=nameWithType> hodnotu do aktuální buňky, pokud lze upravovat buňky. Ve výchozím nastavení, hodnota zobrazovat <xref:System.DBNull> hodnota je hodnota buňky <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> platit pro aktuální buňku.|  
  
### <a name="selection-keys"></a>Výběr klíče

 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, změna aktuální buňky pomocí navigačních kláves změní výběr do nové buňky. Toto chování neovlivňují SHIFT, CTRL a ALT – klávesy.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, stejné chování, ale s těmito přídavky.  
  
|Klávesy nebo kombinace kláves|Popis|  
|----------------------------|-----------------|  
|SHIFT + MEZERNÍK|Vybere celý řádek nebo sloupec (stejného jako je jako kliknutí na záhlaví sloupce či řádku).|  
|klíč navigace (šipka, sloupce stránky vzrůstu HOME, END)|Pokud je vybrán celého řádku nebo sloupce, změnit aktuální buňky na nový řádek nebo sloupec posune výběr úplné nového řádku nebo sloupce (v závislosti na režimu výběru).|  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, změnit aktuální buňky na nový řádek nebo sloupec pomocí klávesnice posune výběr úplné nového řádku nebo sloupce. Toto chování neovlivňují SHIFT, CTRL a ALT – klávesy.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true`, chování navigace nezmění, ale navigaci pomocí klávesnice, při stisknutí klávesy SHIFT (včetně CTRL + SHIFT) slouží k úpravě výběru více buněk. Před zahájením navigační ovládací prvek aktuální buňky označí jako na buňku ukotvení. Při navigaci při stisknutí klávesy SHIFT výběr zahrnuje všechny buňky mezi ukotvení buňky a buňku aktuální. Ostatní buňky v ovládacím prvku zůstane vybrané v případě, že již vybrána, ale mohou být zrušen výběr cesty pokud navigační klávesnice dočasně vloží mezi ukotvení buňky a buňku aktuální je.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, chování ukotvení buňky a aktuální buňky je stejný, ale budou vybrané nebo zrušení výběru pouze úplné řádky nebo sloupce.  
  
## <a name="default-mouse-handling"></a>Výchozí zpracování myši
  
### <a name="basic-mouse-handling"></a>Zpracování základ.
  
> [!NOTE]
>  Vždy kliknete na buňku s levým tlačítkem myši se změní aktuální buňky. Klepnutím pravým tlačítkem myši na buňku otevře místní nabídku, když je k dispozici.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Levé tlačítko myši dolů|Díky buňku kliknutí na aktuální buňku a vyvolává <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> událostí.|  
|Levé tlačítko myši nahoru|Vyvolá <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> událostí|  
|Klikněte na tlačítko levé tlačítko myši.|Vyvolá <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> události|  
|Levé tlačítko myši dolů a přetáhněte na buňky záhlaví sloupce|Pokud <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost `true`, přesune sloupce, takže ji můžete přetáhnout do nové pozice.|  
  
### <a name="mouse-selection"></a>Výběr myši

 Žádný výběr chování je přidružen prostřední tlačítko myši nebo kolečka myši.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, očekávejte toto chování.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Klikněte na tlačítko levé tlačítko myši.|Pokud uživatel klikne na buňku, vybere pouze aktuální buňku. Žádný výběr chování když uživatel klikne záhlaví sloupce či řádku.|  
|Klikněte pravým tlačítkem myši|Zobrazí místní nabídku, pokud je k dispozici.|  
  
 Stejné chování při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, s tím rozdílem, že v závislosti na režimu výběru kliknutím na záhlaví sloupce či řádku výběr celého řádku nebo sloupce, který se nastavení aktuální buňky do první buňky v řádku nebo sloupce.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknutím na libovolnou buňku v řádku nebo sloupce vybere celý řádek nebo sloupec.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true`, kliknete na buňku při stisknutí klávesy CTRL nebo SHIFT slouží k úpravě výběru více buněk.  
  
 Když kliknete na buňku při stisknutí klávesy CTRL, buňky zatímco všechny ostatní buňky zachovat jejich aktuální stav výběru změní jeho stav výběru.  
  
 Když kliknete na buňku nebo sadu buněk při stisknutí klávesy SHIFT, výběr zahrnuje všechny buňky mezi aktuální buňky a na buňku ukotvení na pozici aktuální buňky před prvním kliknutí. Klikněte a tažením ukazatele více buněk, buňku ukotvení při buňku klikli na začátku operace přetažení. Následné kliknutí při stisknutí klávesy SHIFT změnit aktuální buňky, ale ne buňku ukotvení. Ostatní buňky v ovládacím prvku zůstane vybrané v případě, že již vybrána, ale mohou být zrušen výběr cesty pokud navigační myši dočasně vloží mezi ukotvení buňky a buňku aktuální je.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, kliknutím na záhlaví sloupce či řádku (v závislosti na výběru režimu) při stisknutí klávesy SHIFT změní stávající výběr celé řádky nebo sloupce, pokud takové Výběr existuje. V opačném případě bude zrušte výběr a začít nový výběr úplné řádků nebo sloupců. Kliknutím na záhlaví sloupce či řádku při stisknutí klávesy CTRL, ale přidá nebo odebere kliknutí na řádku nebo sloupce z aktuálního výběru bez jiné změny aktuálního výběru.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknete na buňku při stisknutí klávesy SHIFT nebo CTRL se chová stejně jako s výjimkou, že pouze plně řádky a sloupce se nekonzistence týká.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
