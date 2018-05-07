---
title: Přehled vlastnosti AutoSize
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: d7502d11c6cad526c5b19ea2d98e39756d518b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="autosize-property-overview"></a>Přehled vlastnosti AutoSize
<xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost umožňuje změnit jeho velikost, pokud je to nezbytné, aby bylo možné hodnotu zadanou pomocí ovládacího prvku <xref:System.Windows.Forms.Control.PreferredSize%2A> vlastnost. Upravit chování nastavení velikosti pro konkrétní ovládací prvky podle nastavení `AutoSizeMode` vlastnost.  
  
## <a name="autosize-behavior"></a>Chování AutoSize  
 Pouze některé ovládací prvky podporují <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Kromě toho některé ovládací prvky podporující <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporovat i `AutoSizeMode` vlastnost.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Vytváří poněkud různé chování v závislosti na určitý ovládací prvek typ a hodnotu vlastnosti `AutoSizeMode` vlastnost, pokud existuje vlastnost. Následující tabulka popisuje chování, které jsou vždy hodnotu true a obsahuje stručný popis jednotlivých:  
  
|Chování vždy hodnotu true.|Popis|  
|--------------------------|-----------------|  
|Automatická změna velikosti je běhové funkce.|To znamená, že se nikdy zvětšování nebo zmenšuje ovládacího prvku a pak nemá žádný efekt Další.|  
|Pokud se ovládací prvek změní velikost, hodnota jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost vždy zůstává konstantní.|Pokud obsah ovládacího prvku způsobit, že ho růst, ovládacího prvku zvětšování směrem doprava a směrem dolů. Ovládací prvky nejsou růst vlevo.|  
|<xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti jsou přijmout, kdy <xref:System.Windows.Forms.Control.AutoSize%2A> je `true`.|Hodnota ovládacího prvku <xref:System.Windows.Forms.Control.Location%2A> vlastnost se upraví na správnou hodnotu.<br /><br /> **Poznámka:** <xref:System.Windows.Forms.Label> řízení je výjimka, která má toto pravidlo. Pokud nastavíte hodnotu ukotveného <xref:System.Windows.Forms.Label> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`, <xref:System.Windows.Forms.Label> nebude roztažení ovládacího prvku.|  
|Ovládací prvek <xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnosti se vždy dodržují bez ohledu na hodnotu z její <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|<xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnosti nemá vliv <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|  
|Není k dispozici minimální velikost ve výchozím nastavení.|To znamená, že pokud ovládacího prvku je nastavený na zmenšit pod <xref:System.Windows.Forms.Control.AutoSize%2A> a nemá žádný obsah, hodnotu jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost je 0,0. V takovém případě zmenší vlastního ovládacího prvku do bodu, a nebude snadno viditelná.|  
|Pokud ovládací prvek neimplementuje <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda vrátí poslední hodnotu přiřazenou <xref:System.Windows.Forms.Control.Size%2A> vlastnost.|To znamená, že nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> k `true` nebude mít žádný vliv.|  
|V ovládacím prvku <xref:System.Windows.Forms.TableLayoutPanel> zmenší, aby se vešla do buňky do buňky vždy jeho <xref:System.Windows.Forms.Control.MinimumSize%2A> je dosaženo.|Tato velikost je vynucená jako maximální velikost. To tak není při buňky je součástí <xref:System.Windows.Forms.SizeType.AutoSize> sloupce či řádku.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode – vlastnost  
 `AutoSizeMode` Vlastnost poskytuje jemně odstupňovanou kontrolu nad výchozí <xref:System.Windows.Forms.Control.AutoSize%2A> chování. `AutoSizeMode` Vlastnost určuje, jak ovládacího prvku velikostí sám sebe na jeho obsah. Obsah, například může být text pro <xref:System.Windows.Forms.Button> podřízených ovládacích prvků pro kontejner nebo ovládací prvek.  
  
 Následující tabulce je zobrazena <xref:System.Windows.Forms.AutoSizeMode> nastavení a popis chování elicits jednotlivých nastavení.  
  
|AutoSizeMode nastavení|Chování|  
|--------------------------|--------------|  
|GrowAndShrink|Ovládací prvek zvětšováním nebo zmenšováním zahrnuje její obsah.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> a <xref:System.Windows.Forms.Control.MaximumSize%2A> hodnoty jsou ignorovány, ale aktuální hodnota <xref:System.Windows.Forms.Control.Size%2A> vlastnost je ignorována.<br /><br /> Toto je stejné chování jako ovládacích prvků pomocí <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a ne `AutoSizeMode` vlastnost.|  
|GrowOnly|Ovládací prvek zvětšování co nejvíce potřeba zahrnovat její obsah, ale nebude menší než hodnota zadaná podle zmenšit jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost.<br /><br /> Toto je výchozí hodnota pro `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>Ovládací prvky, které podporují s vlastností AutoSize  
 Následující tabulka uvádí prvky, které podporují <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.  
  
|Podpora AutoSize|– Typ ovládacího prvku|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporována.<br />-Již `AutoSizeMode` vlastnost.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> základní)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporována.<br />-   `AutoSizeMode` vlastnost podporována.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Již <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>AutoSize v prostředí návrhu  
 Následující tabulka popisuje chování nastavení velikosti ovládacího prvku v době návrhu na základě hodnoty z jeho <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.  
  
 Přepsání <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> vlastnosti k určení, zda daný ovládací prvek je ve stavu s možností změny velikosti uživatele. V následující tabulce, "nelze" znamená <xref:System.Windows.Forms.Design.SelectionRules.Moveable> pouze "můžete" znamená <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> a <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|Nastavení AutoSize|Nastavení velikosti návrhu gesto|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Již `AutoSizeMode` vlastnost.|Uživatel nemůže změnit velikost ovládacího prvku v době návrhu, s výjimkou následující prvky:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Uživatel nemůže změnit velikost ovládacího prvku v době návrhu.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Uživatel může změnit velikost ovládacího prvku v době návrhu. Když <xref:System.Windows.Forms.Control.Size%2A> vlastnost nastavena, uživatel pouze zvýšit velikost ovládacího prvku.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, nebo <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost skryt.|Uživatel může změnit velikost ovládacího prvku v době návrhu.|  
  
> [!NOTE]
>  Maximalizovat produktivitu, stínů Návrhář formulářů Windows <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost <xref:System.Windows.Forms.Form> třídy. V době návrhu, bude formulář chovat jako když <xref:System.Windows.Forms.Control.AutoSize%2A> je nastavena na `false`, bez ohledu na to jeho skutečného nastavení. V době běhu žádné speciální ubytovací přišla a <xref:System.Windows.Forms.Control.AutoSize%2A> použití vlastnosti je uvedené nastavení vlastností.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
