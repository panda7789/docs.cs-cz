---
title: Přehled vlastnosti AutoSize
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: 6d5c4a22f186ddc5811c4a4d5e79776decea9e50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954294"
---
# <a name="autosize-property-overview"></a>Přehled vlastnosti AutoSize
<xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost na ovládací prvek umožňuje změnit jeho velikost, pokud je to nezbytné, aby bylo možné hodnoty určené <xref:System.Windows.Forms.Control.PreferredSize%2A> vlastnost. Upravit chování nastavení velikosti pro konkrétní ovládací prvky tak, že nastavíte `AutoSizeMode` vlastnost.  
  
## <a name="autosize-behavior"></a>Chování AutoSize  
 Podporovat pouze některé ovládací prvky <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Kromě toho se některé ovládací prvky, které podporují <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost také podporují `AutoSizeMode` vlastnost.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Vlastnost vytváří poněkud liší chování, v závislosti na určitý ovládací prvek typu a hodnoty `AutoSizeMode` vlastnosti, pokud existuje vlastnost. Následující tabulka popisuje chování, které jsou vždy hodnotu true a obsahuje stručný popis jednotlivých:  
  
|Vždy true chování|Popis|  
|--------------------------|-----------------|  
|Automatické velikosti je funkce za běhu.|To znamená, že ho nikdy rozrůstá nebo zmenšuje ovládací prvek a pak nemá žádný další vliv.|  
|Pokud ovládací prvek se změní velikost, hodnota jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost vždy konstantní.|Když obsah ovládacího prvku způsobit, že ji rozšířit, ovládací prvek roste směrem doprava a dolů. Ovládací prvky nejsou rozšiřovat nalevo.|  
|<xref:System.Windows.Forms.Control.Dock%2A> a <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti jsou respektovat, kdy <xref:System.Windows.Forms.Control.AutoSize%2A> je `true`.|Hodnota ovládacího prvku <xref:System.Windows.Forms.Control.Location%2A> vlastnost je upraven na správnou hodnotu.<br /><br /> **Poznámka:** <xref:System.Windows.Forms.Label> ovládací prvek je výjimka tohoto pravidla. Pokud nastavíte hodnotu ukotvený <xref:System.Windows.Forms.Label> ovládacího prvku <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost `true`, <xref:System.Windows.Forms.Label> nebude roztažení ovládacího prvku.|  
|Ovládací prvek <xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnostech vždy se uplatní, bez ohledu na hodnotu jeho <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|<xref:System.Windows.Forms.Control.MaximumSize%2A> a <xref:System.Windows.Forms.Control.MinimumSize%2A> vlastnosti nejsou ovlivněny <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|  
|Není ve výchozím nastavení minimální velikost.|To znamená, že pokud ovládacího prvku nastavená na zmenšit pod <xref:System.Windows.Forms.Control.AutoSize%2A> a nemá žádný obsah, hodnota jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost je 0,0. V tomto případě zmenší ovládacího prvku do bodu, a nebude snadno viditelná.|  
|Pokud ovládací prvek neimplementuje <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda vrátí poslední hodnotu přiřazenou <xref:System.Windows.Forms.Control.Size%2A> vlastnost.|To znamená, že toto nastavení <xref:System.Windows.Forms.Control.AutoSize%2A> k `true` nebude mít žádný efekt.|  
|Ovládací prvek v <xref:System.Windows.Forms.TableLayoutPanel> zmenší podle do buňky do buňky vždy jeho <xref:System.Windows.Forms.Control.MinimumSize%2A> je dosaženo.|Tato velikost se vynucuje maximální velikost. Toto není případ při buňky je součástí <xref:System.Windows.Forms.SizeType.AutoSize> řádku nebo sloupce.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode – vlastnost  
 `AutoSizeMode` Vlastnost poskytuje jemně odstupňovanou kontrolu nad výchozí <xref:System.Windows.Forms.Control.AutoSize%2A> chování. `AutoSizeMode` Vlastnost určuje, jak ovládací prvek velikosti samotného na jeho obsah. Obsah, například může být text <xref:System.Windows.Forms.Button> ovládací prvek nebo podřízené ovládací prvky pro kontejner.  
  
 Následující tabulka ukazuje <xref:System.Windows.Forms.AutoSizeMode> nastavení a popis chování elicits jednotlivých nastavení.  
  
|AutoSizeMode – nastavení|Chování|  
|--------------------------|--------------|  
|GrowAndShrink|Ovládací prvek nebo zmenšováním zahrnuje jeho obsah.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> a <xref:System.Windows.Forms.Control.MaximumSize%2A> hodnoty jsou zachované, ale aktuální hodnota <xref:System.Windows.Forms.Control.Size%2A> vlastnost se ignoruje.<br /><br /> Jedná se o stejné chování jako ovládací prvky s <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost a ne `AutoSizeMode` vlastnost.|  
|GrowOnly|Ovládací prvek roste co nejvíce potřeba zahrnovat obsah, ale nebude menší než hodnotu zadanou pomocí zmenšit jeho <xref:System.Windows.Forms.Control.Size%2A> vlastnost.<br /><br /> Toto je výchozí hodnota pro `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>Ovládací prvky, které podporují s vlastností AutoSize  
 V následující tabulce jsou uvedeny ovládací prvky, které podporují <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.  
  
|Podpora AutoSize|Typ ovládacího prvku|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporována.<br />-Ne `AutoSizeMode` vlastnost.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> základní)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost podporována.<br />-   `AutoSizeMode` vlastnost podporována.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Ne <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>Automaticky přizpůsobit velikost v prostředí návrhu  
 Následující tabulka popisuje chování určení velikosti ovládacího prvku v době návrhu na základě hodnoty z jeho <xref:System.Windows.Forms.Control.AutoSize%2A> a `AutoSizeMode` vlastnosti.  
  
 Přepsat <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> a určí, zda daný ovládací prvek je ve stavu, umožňující změnu velikosti uživatele. V následující tabulce, "nelze" znamená, že <xref:System.Windows.Forms.Design.SelectionRules.Moveable> pouze "můžete" znamená, že <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> a <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|Nastavení AutoSize|Nastavení velikosti návrhu gesta|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Ne `AutoSizeMode` vlastnost.|Uživatel nemůže změnit velikost ovládacího prvku v době návrhu, s výjimkou následujících ovládacích prvků:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Uživatel nemůže změnit velikost ovládacího prvku v době návrhu.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Uživatel může změnit velikost ovládacího prvku v době návrhu. Když <xref:System.Windows.Forms.Control.Size%2A> je hodnota nastavena, uživatel může pouze zvýšit velikost ovládacího prvku.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, nebo <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost je skrytá.|Uživatel může změnit velikost ovládacího prvku v době návrhu.|  
  
> [!NOTE]
>  Maximalizovat produktivitu, stíny Návrháře formulářů Windows <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost <xref:System.Windows.Forms.Form> třídy. V době návrhu, se bude formulář chovat jako by <xref:System.Windows.Forms.Control.AutoSize%2A> je nastavena na `false`, bez ohledu na jeho skutečná nastavení. V době běhu je provedena žádné speciální ubytování a <xref:System.Windows.Forms.Control.AutoSize%2A> použita vlastnost podle nastavení vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.PreferredSize%2A>
- <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
