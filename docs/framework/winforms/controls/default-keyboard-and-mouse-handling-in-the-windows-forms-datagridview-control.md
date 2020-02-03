---
title: Výchozí zpracování klávesnice a myši v ovládacím prvku DataGridView
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
ms.openlocfilehash: 36defff02450b40265c9b6801380cab78eabe5f3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746114"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Výchozí zpracování klávesnice a myši v ovládacím prvku DataGridView model Windows Forms

Následující tabulky popisují, jak mohou uživatelé pracovat s ovládacím prvkem <xref:System.Windows.Forms.DataGridView> prostřednictvím klávesnice a myši.  
  
> [!NOTE]
> K přizpůsobení chování klávesnice můžete zpracovávat standardní události klávesnice, jako je <xref:System.Windows.Forms.Control.KeyDown>. V režimu úprav však ovládací prvek hostované úpravy obdrží vstup z klávesnice a události klávesnice nejsou k dis<xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Chcete-li zpracovat události úprav ovládacího prvku, připojte obslužné rutiny k ovládacímu prvku pro úpravy v obslužné rutině události <xref:System.Windows.Forms.DataGridView.EditingControlShowing>. Alternativně můžete přizpůsobit chování klávesnice v <xref:System.Windows.Forms.DataGridView> podtřídou přepsáním metod <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> a <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>.  
  
## <a name="default-keyboard-handling"></a>Výchozí zpracování klávesnice  
  
### <a name="basic-navigation-and-entry-keys"></a>Základní navigační a vstupní klíče  
  
|Kombinace kláves nebo klíčů|Popis|  
|----------------------------|-----------------|  
|ŠIPKA DOLŮ|Přesune fokus na buňku přímo pod aktuální buňkou. Pokud je fokus na posledním řádku, neprovede žádnou akci.|  
|ŠIPKA VLEVO|Přesune fokus na předchozí buňku v řádku. Pokud je fokus v první buňce řádku, neprovede žádnou akci.|  
|ŠIPKA DOPRAVA|Přesune fokus na další buňku na řádku. Pokud je fokus v poslední buňce řádku, neprovede žádnou akci.|  
|ŠIPKA NAHORU|Přesune fokus na buňku přímo nad aktuální buňkou. Pokud je fokus v prvním řádku, neprovede žádnou akci.|  
|DOMOVSKÁ STRÁNKA|Přesune fokus na první buňku v aktuálním řádku.|  
|END|Přesune fokus na poslední buňku v aktuálním řádku.|  
|O STRÁNKU DOLŮ|Posune ovládací prvek dolů o počet zobrazených řádků, které jsou plně zobrazeny. Přesune fokus na poslední plně zobrazený řádek bez změny sloupců.|  
|O STRÁNKU NAHORU|Posune ovládací prvek nahoru o počet zobrazených řádků, které jsou plně zobrazeny. Přesune fokus na první zobrazený řádek bez změny sloupců.|  
|TAB|Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `false`, přesune fokus na další buňku na aktuálním řádku. Pokud je fokus již v poslední buňce řádku, přesune fokus na první buňku v dalším řádku. Pokud je fokus v poslední buňce ovládacího prvku, přesune fokus na další ovládací prvek v pořadí prvků nadřazeného kontejneru.<br /><br /> Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `true`, přesune fokus na další ovládací prvek v pořadí prvků nadřazeného kontejneru.|  
|SHIFT+TAB|Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `false`, přesune fokus na předchozí buňku na aktuálním řádku. Pokud je fokus již v první buňce řádku, přesune fokus na poslední buňku v předchozím řádku. Pokud je fokus v první buňce v ovládacím prvku, přesune fokus na předchozí ovládací prvek v pořadí prvků nadřazeného kontejneru.<br /><br /> Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `true`, přesune fokus na předchozí ovládací prvek v pořadí prvků nadřazeného kontejneru.|  
|CTRL+TAB|Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `false`, přesune fokus na další ovládací prvek v pořadí prvků nadřazeného kontejneru.<br /><br /> Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `true`, přesune fokus na další buňku na aktuálním řádku. Pokud je fokus již v poslední buňce řádku, přesune fokus na první buňku v dalším řádku. Pokud je fokus v poslední buňce ovládacího prvku, přesune fokus na další ovládací prvek v pořadí prvků nadřazeného kontejneru.|  
|CTRL+SHIFT+TAB|Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `false`, přesune fokus na předchozí ovládací prvek v pořadí prvků nadřazeného kontejneru.<br /><br /> Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.StandardTab%2A> `true`, přesune fokus na předchozí buňku na aktuálním řádku. Pokud je fokus již v první buňce řádku, přesune fokus na poslední buňku v předchozím řádku. Pokud je fokus v první buňce v ovládacím prvku, přesune fokus na předchozí ovládací prvek v pořadí prvků nadřazeného kontejneru.|  
|CTRL + ŠIPKA|Přesune fokus na nejvzdálenější buňku ve směru šipky.|  
|CTRL + HOME|Přesune fokus na první buňku v ovládacím prvku.|  
|CTRL + END|Přesune fokus na poslední buňku v ovládacím prvku.|  
|CTRL + PAGEDOWN + ŠIPKA NAHORU|Stejné jako PAGE DOWN nebo PAGE UP.|  
|F2|Vloží aktuální buňku do režimu úprav buňky, pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.EditMode%2A> <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> nebo <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Seřadí aktuální sloupec, pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Je stejný jako při kliknutí na záhlaví aktuálního sloupce. K dispozici od .NET Framework 4.7.2. Chcete-li povolit tuto funkci, musí být aplikace cíleny na .NET Framework 4.7.2 nebo novější verze, nebo explicitně zapínat do vylepšení přístupnosti pomocí přepínačů AppContext.|  
|F4|Pokud je aktuální buňka <xref:System.Windows.Forms.DataGridViewComboBoxCell>, převede buňku do režimu úprav a zobrazí rozevírací seznam.|  
|ALT + ŠIPKA NAHORU/DOLŮ|Pokud je aktuální buňka <xref:System.Windows.Forms.DataGridViewComboBoxCell>, převede buňku do režimu úprav a zobrazí rozevírací seznam.|  
|MEZERNÍK|Pokud je aktuální buňka <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>nebo <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, vyvolá události <xref:System.Windows.Forms.DataGridView.CellClick> a <xref:System.Windows.Forms.DataGridView.CellContentClick>. Pokud je aktuální buňka <xref:System.Windows.Forms.DataGridViewButtonCell>, přestiskne také tlačítko. Pokud je aktuální buňka <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, změní se také stav check.|  
|NAPIŠTE|Potvrdí všechny změny v aktuální buňce a řádku a přesune fokus na buňku přímo pod aktuální buňkou. Pokud je fokus na posledním řádku, potvrdí všechny změny bez přesunutí fokusu.|  
|ESC|Pokud je ovládací prvek v režimu úprav, aplikace zruší úpravy. Pokud ovládací prvek není v režimu úprav, vrátí všechny změny provedené na aktuálním řádku, pokud je ovládací prvek svázán se zdrojem dat, který podporuje úpravy nebo virtuální režim, s rozsahem potvrzení na úrovni řádku.|  
|BACKSPACE|Odstraní znak před bodem vložení při úpravě buňky.|  
|DELETE|Odstraní znak za kurzorem při úpravě buňky.|  
|CTRL + ENTER|Potvrdí všechny změny v aktuální buňce bez přesunutí fokusu. Také potvrdí všechny změny aktuálního řádku, pokud je ovládací prvek svázán se zdrojem dat, který podporuje úpravy nebo virtuální režim, s rozsahem potvrzení na úrovni řádků.|  
|CTRL + 0|Zadá hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType> do aktuální buňky, pokud je možné upravit buňku. Ve výchozím nastavení je hodnota zobrazení hodnoty <xref:System.DBNull> buňky hodnotou vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> v platnosti pro aktuální buňku.|  
  
### <a name="selection-keys"></a>Klávesy pro výběr

 Pokud je vlastnost <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavena na hodnotu `false` a vlastnost <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, změna aktuální buňky pomocí navigačních kláves změní výběr na novou buňku. Klávesy SHIFT, CTRL a ALT toto chování neovlivňují.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, dojde k stejnému chování, ale s následujícími přídavky.  
  
|Kombinace kláves nebo klíčů|Popis|  
|----------------------------|-----------------|  
|SHIFT + MEZERNÍK|Vybere celý řádek nebo sloupec (stejné jako při kliknutí na záhlaví řádku nebo sloupce).|  
|navigační klíč (šipkový klíč, stránka nahoru/dolů, HOME, END)|Pokud je vybrán celý řádek nebo sloupec, změna aktuální buňky na nový řádek nebo sloupec přesune výběr na celý nový řádek nebo sloupec (v závislosti na režimu výběru).|  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavená na `false` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, změna aktuální buňky na nový řádek nebo sloupec pomocí klávesnice přesune výběr na celý nový řádek nebo sloupec. Klávesy SHIFT, CTRL a ALT toto chování neovlivňují.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastaveno na `true`, navigační chování se nezmění, ale navigace pomocí klávesnice při stisknutí klávesy SHIFT (včetně kláves CTRL + SHIFT) upraví výběr více buněk. Před zahájením navigace ovládací prvek označí aktuální buňku jako kotvicí buňku. Když při stisknutí klávesy SHIFT procházíte, výběr zahrnuje všechny buňky mezi buňkou ukotvení a aktuální buňkou. Ostatní buňky v ovládacím prvku zůstanou vybrány, pokud již byly vybrány, ale mohou být nezaškrtnuté, pokud je navigace klávesnicí dočasně umístěna mezi buňkou ukotvení a aktuální buňkou.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavené na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, chování buňky ukotvení a aktuální buňky je stejné, ale vybrané nebo nevybrané sloupce se vyberou.  
  
## <a name="default-mouse-handling"></a>Výchozí zpracování myší
  
### <a name="basic-mouse-handling"></a>Základní zpracování myši
  
> [!NOTE]
> Kliknutí na buňku s levým tlačítkem myši vždy změní aktuální buňku. Kliknutím pravým tlačítkem myši na buňku otevřete místní nabídku, jakmile bude k dispozici.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Levé tlačítko myši dolů|Nastaví buňku po kliknutí na aktuální buňku a vyvolá událost <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>.|  
|Levé tlačítko myši nahoru|Vyvolá událost <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType>.|  
|Kliknutí levým tlačítkem myši|Vyvolává události <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>.|  
|Levé tlačítko myši a přetáhnutí na buňku záhlaví sloupce|Pokud je vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> `true`, přesune sloupec, aby jej bylo možné vyřadit do nové pozice.|  
  
### <a name="mouse-selection"></a>Výběr myši

 Žádné chování při výběru není přidruženo k prostřednímu tlačítku myši nebo kolečkem myši.  
  
 Pokud je vlastnost <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavena na hodnotu `false` a vlastnost <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, dojde k následujícímu chování.  
  
|Akce myši|Popis|  
|------------------|-----------------|  
|Kliknutí levým tlačítkem myši|Vybere pouze aktuální buňku, pokud uživatel klikne na buňku. Žádné chování při výběru, pokud uživatel klikne na záhlaví řádku nebo sloupce.|  
|Kliknutí pravým tlačítkem myši|Zobrazí místní nabídku, je-li k dispozici.|  
  
 K tomuto chování dochází, když je <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> nastaveno na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, s výjimkou toho, že v závislosti na režimu výběru se kliknutím na záhlaví řádku nebo sloupce vybere celý řádek nebo sloupec a nastaví se aktuální buňka na první buňku v řádku nebo sloupci.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, kliknutím na libovolnou buňku v řádku nebo sloupci se vybere celý řádek nebo sloupec.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastaveno na `true`, kliknutím na buňku v kombinaci kláves CTRL + SHIFT upravíte výběr více buněk.  
  
 Když při stisknutí klávesy CTRL kliknete na buňku, změní se její stav výběru, zatímco všechny ostatní buňky si budou uchovávat svůj aktuální stav výběru.  
  
 Když při stisknutí klávesy SHIFT kliknete na buňku nebo řadu buněk, výběr zahrnuje všechny buňky mezi aktuální buňkou a ukotvenou buňkou umístěnou na pozici aktuální buňky před prvním kliknutím. Když kliknete na ukazatel myši a přetáhnete ho mezi více buněk, buňka ukotvení je buňka, na které se na začátku operace přetažení klikne. Následné kliknutí při stisknutí klávesy SHIFT změní aktuální buňku, ale ne buňku ukotvení. Ostatní buňky v ovládacím prvku zůstanou vybrány, pokud již byly vybrány, ale mohou být nezaškrtnuté, pokud je navigace myší dočasně umístěna mezi buňkou ukotvení a aktuální buňkou.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavená na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, klikněte na záhlaví řádku nebo sloupce (v závislosti na režimu výběru) a při stisknutí klávesy SHIFT se změní stávající výběr celých řádků nebo sloupců, pokud takový výběr existuje. V opačném případě Smaže výběr a spustí nový výběr celých řádků nebo sloupců. Po kliknutí na záhlaví řádku nebo sloupce se ale při stisknutí klávesy CTRL přidají nebo odeberou vybraný řádek nebo sloupec z aktuálního výběru bez dalších úprav aktuálního výběru.  
  
 Pokud je <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavená na `true` a <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, klikne na buňku, zatímco stisknutí klávesy SHIFT nebo CTRL se chová stejným způsobem s tím rozdílem, že jsou ovlivněné jenom celé řádky a sloupce.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
