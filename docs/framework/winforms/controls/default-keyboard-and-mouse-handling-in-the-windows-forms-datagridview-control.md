---
title: Výchozí zpracování v ovládacím prvku Windows Forms DataGridView klávesnice a myši
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
ms.openlocfilehash: b0ed468fe7d38fbeda90d5347338bce14059b730
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529565"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Výchozí zpracování v ovládacím prvku Windows Forms DataGridView klávesnice a myši

Následující tabulky popisují, jak mohou uživatelé komunikovat s <xref:System.Windows.Forms.DataGridView> řízení prostřednictvím klávesnici a myš.  
  
> [!NOTE]
>  Chcete-li přizpůsobit chování klávesnice, lze zpracovat události standardní klávesnice, jako <xref:System.Windows.Forms.Control.KeyDown>. V režimu úprav, ale hostované ovládací prvek úprav přijímá vstupu klávesnice a události klávesnice pro nedojde k <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pro zpracování úprav události ovládacího prvku, připojení vaší obslužné rutiny do ovládacího prvku úprav v <xref:System.Windows.Forms.DataGridView.EditingControlShowing> obslužné rutiny události. Alternativně můžete přizpůsobit chování klávesnice v <xref:System.Windows.Forms.DataGridView> podtřídami přepsáním <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> a <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> metody.  
  
## <a name="default-keyboard-handling"></a>Výchozí zpracování klávesnice  
  
### <a name="basic-navigation-and-entry-keys"></a>Základní navigaci a položka klíče  
  
|Klíč nebo kombinaci kláves|Popis|  
|----------------------------|-----------------|  
|ŠIPKA DOLŮ|Přejdete k buňky přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, neprovede žádnou akci.|  
|ŠIPKA DOLEVA|Přejdete k předchozí buňky v řádku. Pokud je zaměření v první buňky v řádku, neprovede žádnou akci.|  
|ŠIPKA DOPRAVA|Přejdete k dalším buňky v řádku. Pokud je zaměření v poslední buňky v řádku, neprovede žádnou akci.|  
|ŠIPKA NAHORU|Přejdete k buňky přímo nad aktuální buňky. Pokud je zaměření na prvním řádku, neprovede žádnou akci.|  
|DOMOVSKÉ|Přejdete k první buňky na aktuálním řádku.|  
|END|Přejdete na poslední buňku na aktuálním řádku.|  
|PAGE DOWN|Posune ovládací prvek dolů podle počtu řádků, které jsou plně zobrazené. Změní na aktivní poslední řádek plně zobrazených beze změny sloupců.|  
|PAGE UP|Posune ovládacího prvku nahoru podle počtu řádků, které jsou plně zobrazené. Přesun zaměření na první řádek zobrazených beze změny sloupců.|  
|KARTA|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přejdete k dalším buňky na aktuálním řádku. Pokud je zaměření již poslední buňky řádku, přejdete k první buňky v dalším řádku. Pokud je zaměření v poslední buňky v ovládacím prvku, přejdete na další ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přejdete k další ovládací prvek v pořadí nadřazeného kontejneru.|  
|SHIFT + TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přejdete k předchozí buňku na aktuálním řádku. Pokud je zaměření již první buňky řádku, přejdete k poslední buňky v předchozím řádku. Pokud je zaměření v první buňky v ovládacím prvku, přejdete k předchozí ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přejdete k předchozí ovládací prvek v pořadí nadřazeného kontejneru.|  
|CTRL+TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přejdete k další ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přejdete k dalším buňky na aktuálním řádku. Pokud je zaměření již poslední buňky řádku, přejdete k první buňky v dalším řádku. Pokud je zaměření v poslední buňky v ovládacím prvku, přejdete na další ovládací prvek v pořadí nadřazeného kontejneru.|  
|CTRL+SHIFT+TAB|Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `false`, přejdete k předchozí ovládací prvek v pořadí nadřazeného kontejneru.<br /><br /> Pokud <xref:System.Windows.Forms.DataGridView.StandardTab%2A> hodnota vlastnosti je `true`, přejdete k předchozí buňku na aktuálním řádku. Pokud je zaměření již první buňky řádku, přejdete k poslední buňky v předchozím řádku. Pokud je zaměření v první buňky v ovládacím prvku, přejdete k předchozí ovládací prvek v pořadí nadřazeného kontejneru.|  
|CTRL + ŠIPKA|Přejdete k nejvíce buňky ve směru na šipku.|  
|CTRL + HOME|Přejdete k první buňky v ovládacím prvku.|  
|CTRL + END|Přejdete k poslední buňky v ovládacím prvku.|  
|CTRL + STRÁNKU DOLŮ/NAHORU|Stejné jako PAGE DOWN nebo PAGE UP.|  
|F2|Uloží aktuální buňky do buňky režimu úprav, pokud <xref:System.Windows.Forms.DataGridView.EditMode%2A> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> nebo <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Seřadí aktuální sloupec, pokud <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> hodnota vlastnosti je <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Je stejný jako při kliknutí na aktuální záhlaví sloupce. Dostupné od verze rozhraní .NET Framework 4.7.2. Chcete-li povolit tuto funkci, musí aplikace cílí na rozhraní .NET Framework 4.7.2 nebo novější verze nebo explicitně účast v vylepšení přístupnosti pomocí přepínačů AppContext.|  
|F4|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umístí buňky do režimu úprav a zobrazí se seznam rozevíracího seznamu.|  
|ŠIPKA ALT + ŠIPKA NAHORU NEBO DOLŮ|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewComboBoxCell>, umístí buňky do režimu úprav a zobrazí se seznam rozevíracího seznamu.|  
|MÍSTO|Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, nebo <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, vyvolá <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellContentClick> události. Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewButtonCell>, také tlačítka. Pokud je aktuální buňky <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, také změní stav kontroly.|  
|ZADEJTE|Potvrdí změny aktuální buňky a buňku a přejdete k buňky přímo pod aktuální buňky. Pokud je zaměření na posledním řádku, potvrdí změny bez přesouvání fokus.|  
|ESC|Pokud ovládací prvek je v režimu úprav, zruší úpravy. Pokud ovládací prvek není v režimu úprav, vrátí všechny změny, které byly provedeny na aktuálním řádku Pokud ovládací prvek vázán na zdroj dat, který podporuje úpravy nebo byl implementován virtuálního režimu s oborem potvrzení na úrovni řádků.|  
|BACKSPACE|Při úpravě buňku k odstranění znaku před ním.|  
|DELETE|Při úpravě buňku k odstranění znaku po kurzor.|  
|CTRL + ENTER|Neprovede žádné změny aktuální buňky bez přesouvání fokus. Také potvrzení všechny změny na aktuálním řádku, pokud je ovládací prvek vázán ke zdroji dat, který podporuje režim úprav nebo virtuální byl implementován s nízkoúrovňové potvrzení oboru.|  
|CTRL + 0|Zadá <xref:System.DBNull.Value?displayProperty=nameWithType> hodnotu do aktuální buňky, pokud lze upravovat buňky. Ve výchozím zobrazení hodnota <xref:System.DBNull> hodnotu buňky je hodnota <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> platí pro aktuální buňky.|  
  
### <a name="selection-keys"></a>Výběr klíče

 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, změna aktuální buňky pomocí navigační klávesy změní výběr na nové buňky. SHIFT, CTRL a ALT – klávesy neovlivní toto chování.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, dojde k stejné chování, ale s těmito přídavky.  
  
|Klíč nebo kombinaci kláves|Popis|  
|----------------------------|-----------------|  
|SHIFT + MEZERNÍK|Vybere celý řádek nebo sloupec, (stejný jako při kliknutí záhlaví sloupce či řádku).|  
|navigace klíč (šipka klíč, sloupce vzrůstu stránky, domů, END)|Pokud je vybrána úplný řádek nebo sloupec, změna aktuální buňky na nový řádek nebo sloupec pohyb úplné nového řádku nebo sloupce (v závislosti na režimu výběru).|  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, změna aktuální buňky do nového řádku nebo sloupce pomocí klávesnice posune výběr úplné nový řádek nebo sloupec. SHIFT, CTRL a ALT – klávesy neovlivní toto chování.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `true`, nezmění chování navigace, ale navigaci pomocí klávesnice, při stisknutí klávesy SHIFT (včetně CTRL + SHIFT) slouží k úpravě výběru více buněk. Před zahájením navigace, ovládacího prvku označí aktuální buňky jako anchor buňky. Když přejdete při stisknutí klávesy SHIFT, výběr zahrnuje všechny buňky mezi buňky ukotvení a aktuální buňky. Pokud již vybrána, ale mohou být nezaškrtnuté Pokud navigační klávesnice dočasně zapisuje mezi buňky ukotvení a aktuální buňky je, zůstane vybrané jiných buněk v ovládacím prvku.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, chování ukotvení buňky a aktuální buňky je stejný, ale stát vybrané pouze úplná řádky nebo sloupce nebo zrušit.  
  
## <a name="default-mouse-handling"></a>Výchozí zpracování myši
  
### <a name="basic-mouse-handling"></a>Zpracování základní myši
  
> [!NOTE]
>  Klepnutím na buňku levé tlačítko vždy změní aktuální buňky. Klepnutím pravým tlačítkem myši na buňku otevře místní nabídky, když je k dispozici.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Levé tlačítko myši směrem dolů|Vytvoří kliknutelnou buňky aktuální buňky a vyvolá <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> událostí.|  
|Levé tlačítko nahoru|Vyvolá <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> událostí|  
|Levým tlačítkem myši klikněte na|Vyvolá <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> události|  
|Levé tlačítko myši směrem dolů a přetáhněte na buňku záhlaví sloupců|Pokud <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost je `true`, přesune sloupce, takže může být přetažen do nového umístění.|  
  
### <a name="mouse-selection"></a>Výběr myši

 Žádné chování výběru je přidružen tlačítko střední myši nebo kolečko myši.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, očekávejte toto chování.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Klikněte na levé tlačítko myši|Vybere pouze aktuální buňky, pokud uživatel klikne na buňku. Žádné chování výběru Pokud uživatel kliknutím na záhlaví sloupce či řádku.|  
|Klikněte pravým tlačítkem myši|Místní nabídky zobrazí, pokud je k dispozici.|  
  
 Stejné chování dochází při <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>kromě toho, že v závislosti na režimu výběru kliknutím na záhlaví sloupce či řádku vyberte úplný řádek nebo sloupec, který se nastavení aktuální buňky do první buňky v sloupce či řádku.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknutím na libovolnou buňku ve sloupce či řádku vybere celý řádek nebo sloupec.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `true`, klikněte na buňku při stisknutí klávesy CTRL nebo SHIFT slouží k úpravě výběru více buněk.  
  
 Po kliknutí na tlačítko buňku při stisknutím kombinace kláves CTRL buňky se změní stav výběru při všech ostatních buněk zachovat jejich aktuální stav výběru.  
  
 Po kliknutí na tlačítko buňku nebo řady buněk při stisknutí klávesy SHIFT, výběr zahrnuje všechny buňky mezi aktuální buňky a buňku ukotvení na pozici aktuální buňky před první klikněte na tlačítko. Klikněte a přetáhněte ukazatele napříč více buněk, buňky ukotvení při buňky klikli na začátku operace přetažení. Následující klepnutí při stisknutí klávesy SHIFT změnit aktuální buňky, ale ne buňky ukotvení. Pokud již vybrána, ale mohou být nezaškrtnuté Pokud navigační myši dočasně zapisuje mezi buňky ukotvení a aktuální buňky je, zůstane vybrané jiných buněk v ovládacím prvku.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, kliknutím na záhlaví sloupce či řádku (v závislosti na režimu výběru) při stisknutí klávesy SHIFT změní stávající výběr úplné řádků nebo sloupců, pokud takové Výběr existuje. Jinak bude zrušte zaškrtnutí políčka a spusťte nový výběr úplné řádků nebo sloupců. Kliknutím na záhlaví sloupce či řádku a stisknutím klávesy CTRL, ale bude přidat nebo odebrat sloupce či řádku kliknutelnou z aktuálního výběru beze změny jinak aktuální výběr.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastaven na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, klikněte na buňku a stisknutím klávesy SHIFT nebo CTRL se chová stejně jako s výjimkou tohoto pouze úplná řádků a sloupců se vztahuje.  
  
## <a name="see-also"></a>Viz také

<xref:System.Windows.Forms.DataGridView>  
 [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
