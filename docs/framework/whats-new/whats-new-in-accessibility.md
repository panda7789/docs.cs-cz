---
title: Co je nového v usnadnění v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Co je nového v usnadnění v rozhraní .NET Framework

Rozhraní .NET Framework se zaměřuje na zpřístupnění aplikace více pro vaše uživatele. Funkce usnadnění povolit aplikace a poskytuje příslušné prostředí pro uživatele technologie usnadnění. Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupná. 

## <a name="accessibility-switches"></a>Usnadnění přepínače

Můžete nakonfigurovat aplikace, který se přidá do funkce pro usnadnění přístupu, pokud se používá starší verze nebo 4.7 rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 nebo novější. Můžete také nakonfigurovat v aplikaci použijte starší verze funkce (a ne využívají funkce pro usnadnění přístupu), pokud je cílem rozhraní .NET Framework 4.7.1 nebo novější. Každá verze rozhraní .NET Framework, která zahrnuje funkce pro usnadnění přístupu má specifické pro verzi usnadnění přepínač, který přidáte do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace. Tady jsou podporované přepínače:

|Version|přepínače|
|---|---|
|Rozhraní .NET framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|Rozhraní .NET framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Využití výhod vylepšení přístupnosti

Nové funkce pro usnadnění přístupu jsou povolené ve výchozím nastavení pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější. Kromě toho aplikace, které cílení na dřívější verzi rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 a později se můžete rozhodnout ze starší verze usnadnění chování (a tím využít výhod vylepšení přístupnosti) přidáním parametrů do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddíl konfiguračního souboru aplikace a nastavení jejich hodnoty `false`. Následující ukazuje, jak se vyjádřit výslovný souhlas pro usnadnění vylepšení byla zavedená v rozhraní .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Pokud zvolíte možnost vyjádřit výslovný souhlas pro funkce usnadnění v novější verzi rozhraní .NET Framework, můžete musí také výslovně vyjádřit výslovný souhlas k funkcím z dřívějších verzí rozhraní .NET Framework. Konfigurace aplikace využívat výhod vylepšení přístupnosti v obou rozhraní .NET Framework 4.7.1 a 4.7.2 vyžaduje následující [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Obnovení staršího chování

Aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7.1 můžete zakázat funkce usnadnění přidáním přepínače se mají [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) část konfigurační soubor aplikace a nastavení jejich hodnoty `true`. Například následující konfigurace výslovný nesouhlas byla zavedená v rozhraní .NET Framework 4.7.2 funkce pro usnadnění přístupu:  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 zahrnuje nové funkce usnadnění v těchto oblastech:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a>Windows Forms

**OS definovaných barev v motivy vysoký kontrast**

Od verze rozhraní .NET Framework 4.7.2, používá Windows Forms barev definovaných podle operačního systému v vysoký kontrast motivů. Tato akce ovlivní následující prvky:

- Šipku rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku.

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavena na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Dříve vybrané barvy textu a pozadí nebyly – kontrast a byly těžko čitelný.

- Ovládací prvky obsažené v <xref:System.Windows.Forms.GroupBox> s jeho <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavena na hodnotu `false`.
 
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, A <xref:System.Windows.Forms.ToolStripDropDownButton> ovládací prvky, které mají vyšší světlost kontrast poměr v režimu Vysoký kontrast.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Vylepšení Předčítání**

Od verze rozhraní .NET Framework 4.7.2, je podpora Předčítání rozšířené následujícím způsobem:

- Vysílal informace o hodnotě <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při uvedení text <xref:System.Windows.Forms.ToolStripMenuItem>. 

- Určuje, kdy <xref:System.Windows.Forms.ToolStripMenuItem> má jeho <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavena na hodnotu `false`.

- Nabízí zpětnou vazbu týkající se stavu zaškrtávacího políčka při <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je nastavena na `true`.

- Program Předčítání na kontrolovat režimu fokus pořadí je konzistentní s visual pořadí prvků v dialogovém okně stahování ClickOnce.

**DataGridView – vylepšení**

Od verze rozhraní .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> ovládací prvek obsahuje zavedla následující vylepšení přístupnosti:

- Řádky lze seřadit pomocí klávesnice. Uživatele můžete použít klávesu F3 Chcete-li řadit podle aktuální sloupec.

- Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, změní barvu, která označuje aktuální sloupec jako karty uživatele prostřednictvím buněk na aktuálním řádku na záhlaví sloupce.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správné nadřazeného ovládacího prvku.

**Vylepšené vizuální upozornění**

- <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastnost zobrazí indikátor fokus při přijetí fokus.

**Podpora vylepšené vlastnost mřížky**

- <xref:System.Windows.Forms.PropertyGrid> Řízení nyní návratový podřízené elementy `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pouze v případě, že je povolená PropertyGrid element.

- <xref:System.Windows.Forms.PropertyGrid> Řízení podřízené elementy návratový `false` pro <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost jenom v případě, že uživatel může změnit PropertyGrid elementu.

**Vylepšené klávesnice navigace**

- <xref:System.Windows.Forms.ToolStripButton> Řízení umožňuje fokus při obsažené v <xref:System.Windows.Forms.ToolStripPanel> který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavena na hodnotu `true`

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Změny ovládacích prvků CheckBox a RadioButton**

V rozhraní .NET Framework 4.7.1 a starší verze, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládacích prvků mají nekonzistentní a v klasickém a Vysoký kontrast motivů, vizuály nesprávný fokus.  Těmto problémům dochází v případech, kdy ovládací prvky nemají žádné sady obsahu.  Přechod mezi motivy matoucí a fokus visual může být obtížné najdete v článku.

V rozhraní .NET Framework 4.7.2 tyto vizuály jsou nyní víc konzistentní v rámci celého motivy a snadno viditelná v klasickém a vysokým kontrastem motivů.

**Ovládací prvky WinForms hostované v aplikaci WPF**

Pro ovládací prvek WinForms hostované v aplikaci WPF v rozhraní .NET Framework 4.7.1 a starší verze, uživatelé nelze kartu mimo vrstvě WinForms Pokud je první nebo poslední ovládací prvek v této vrstvě WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. V rozhraní .NET Framework 4.7.2 mohou uživatelé nyní kartě mimo vrstvě WinForms.

Automatizované aplikace, které závisí na fokus nikdy uvozovací znaky vrstvě WinForms může však přestane fungovat podle očekávání.

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 zahrnuje nové funkce usnadnění v těchto oblastech:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [Ovládací prvky ASP.NET web](#aspnet471)

- [.NET SDK – nástroje](#tools471)

- [Návrhář Windows Workflow Foundation (WF) pracovního postupu](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Vylepšení čtečky obrazovky**

Pokud jsou povolené vylepšení přístupnosti, rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení, které ovlivňují čtečky obrazovky:

- V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.Expander> ovládací prvky byly oznamují čtečky obrazovky jako tlačítka. Od verze rozhraní .NET Framework 4.7.1, že jsou správně oznámila jako rozšíření, sbalitelné skupiny.

- V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.DataGridCell> ovládací prvky byly oznamují čtečky obrazovky jako "vlastní". Od verze rozhraní .NET Framework 4.7.1, se nyní správně odesílány zpět jako buňky v mřížce dat (lokalizované).
 
- Od verze rozhraní .NET Framework 4.7.1, čtečky obrazovky oznamujeme název upravitelné <xref:System.Windows.Controls.ComboBox>.

- V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.PasswordBox> ovládací prvky byly oznámí jako "žádná položka v zobrazení", nebo byl jinak nesprávné chování. Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.

**Vlastnosti UIAutomation LiveRegion podpory**

Čtečky obrazovky například Předčítání pomoci ostatním uživatelům číst obsah uživatelského rozhraní aplikace, obvykle je výstup uživatelského rozhraní obsah, který je aktivní. Ale pokud prvku uživatelského rozhraní se změní a nemá fokus, uživatel nemusí být upozorněni a může dojít důležité informace. Za provozu oblasti cílem řešení tohoto problému. Vývojář může je použít k informování čtečky obrazovky nebo jakéhokoli klienta vlastnosti UIAutomation, který byl proveden důležité změně prvku uživatelského rozhraní. Čtečky obrazovky můžete pak rozhodnout, jak a kdy k informování uživatelů této změny. 

Pro podporu za provozu oblasti, byly přidány následující rozhraní API k použití WPF:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pole, které identifikovat **LiveSetting** vlastnost a **LiveRegionChanged** událostí. Můžete být nastavit s použitím jazyka XAML.

- **AutomationProperties.LiveSetting** přidružená vlastnost, která informuje o čtečky obrazovky významné změny uživatelského rozhraní pro uživatele.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Vlastnost, která ji identifikuje **AutomationProperties.LiveSetting** přidružená vlastnost.
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodu, která může být potlačena za účelem poskytování **LiveSetting** hodnotu.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, které získání a nastavení **LiveSetting** hodnotu.
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Výčtu, který definuje následující možné **LiveSetting** hodnoty:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Element neodešle oznámení, pokud došlo ke změně obsahu oblasti za provozu.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Element odešle-interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Element odešle interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.   

Můžete vytvořit LiveRegion nastavením **AutomationProperties.LiveSetting** vlastnost v elementu zajímat, jak je znázorněno v následujícím příkladu:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Při změně dat v oblasti za provozu a je nutné informovat čtečky obrazovky, explicitně zvýšíte událost, jak znázorňuje následující ukázka.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Vysoký kontrast**

Od verze rozhraní .NET Framework 4.7.1, vysoký kontrast vylepšily do různých ovládacích prvků WPF. Jsou nyní viditelné při <xref:System.Windows.SystemParameters.HighContrast%2A> motiv nastavena. Mezi ně patří:

- <xref:System.Windows.Controls.Expander> Ovládací prvek

    Visual pro zaměřuje <xref:System.Windows.Controls.Expander> ovládací prvek je nyní viditelné. Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.RadioButton> ovládací prvky jsou také viditelné. Příklad:

    Před: 
    
    ![Ovládací prvek Expander s fokusem před vylepšení přístupnosti](media/expander-before.png)

    Po: 

    ![Ovládací prvek Expander fokus po vylepšení přístupnosti](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky
 
    Text v <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky je nyní snazší uvidí, když je vybraný v vysoký kontrast motivů. Příklad:

    Před: 

    ![Vysoký kontrast přepínač s fokusem před vylepšení přístupnosti](media/radio-button-before.png)
    
    Po: 

    ![Vysoký kontrast přepínač s fokusem po vylepšení přístupnosti](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> Ovládací prvek
 
    Od verze rozhraní .NET Framework 4.7.1, ohraničení zakázáno <xref:System.Windows.Controls.ComboBox> ovládací prvek se stejnou barvu jako zakázaný text. Příklad:
    
    Před: 

     ![ComboBox – zakázáno ohraničení a text před vylepšení přístupnosti](media/combo-disabled-before.png)

    Po:   

     ![ComboBox – po vylepšení přístupnosti zakázán ohraničení a text.](media/combo-disabled-after.png)

    Kromě toho zakázané a zaměřují se tlačítka použít barvu motivu správné.

    Před:

    ![Tlačítko barev motivů před vylepšení přístupnosti](media/button-themes-before.png) 
    
    Po: 

    ![Tlačítko barev motivů po vylepšení přístupnosti](media/button-themes-after.png) 

    Nakonec v rozhraní .NET Framework 4.7 a dřívějších verzích, nastavení <xref:System.Windows.Controls.ComboBox> styl ovládacího prvku, který se `Toolbar.ComboBoxStyleKey` způsobila na šipku rozevíracího seznamu byla neviditelná. Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1. Příklad:

    Před: 

    ![Toolbar.ComboBoxStyleKey před vylepšení přístupnosti](media/comboboxstylekey-before.png) 
    
    Po: 

    ![Toolbar.ComboBoxStyleKey po vylepšení přístupnosti](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> Ovládací prvek

    Od verze rozhraní .NET Framework 4.7.1, šipku řazení indikátoru v <xref:System.Windows.Controls.DataGrid> řídí teď používá opravte barev motivů. Příklad:

    Před: 

    ![Řazení šipku indikátoru před vylepšení přístupnosti](media/sort-indicator-before.png) 
    
    Po:   
 
    ![Řazení indikátor šipku po vylepšení přístupnosti](media/sort-indicator-after.png) 
    
    Kromě toho v rozhraní .NET Framework 4.7 a dřívějších verzí, výchozí styl odkaz změnit na nesprávné barva na myši v režimu vysokého kontrastu. Tento problém vyřešen od verze rozhraní .NET Framework 4.7.1. Podobně <xref:System.Windows.Controls.DataGrid> políčko sloupce používá pro zpětnou vazbu fokus klávesnice od verze rozhraní .NET Framework 4.7.1 očekávané barvy.

    Před: 

    ![DataGrid – výchozí odkaz styl před vylepšení přístupnosti](media/default-link-style-before.png) 
 
    Po:    
  
    ![DataGrid – výchozí odkaz styl po vylepšení přístupnosti](media/default-link-style-after.png)  

Další informace o vylepšení přístupnosti grafického subsystému WPF v rozhraní .NET Framework 4.7.1 najdete v tématu [vylepšení přístupnosti v grafickém subsystému WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a>Vylepšení přístupnosti Windows Forms

Windows Forms (WinForms) v rozhraní .NET Framework 4.7.1 zahrnuje změny usnadnění v následujících oblastech.

**Vylepšené zobrazení v režimu vysokého kontrastu**

Od verze rozhraní .NET Framework 4.7.1, nabízejí různé ovládací prvky WinForms vylepšené vykreslování v funkce Vysoký kontrast režimech k dispozici v operačním systému. Windows 10 došlo ke změně hodnoty pro některé barvy systému vysoký kontrast a Windows Forms je založena na rozhraní Windows 10 Win32. Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi systému Windows a vyjádřit výslovný souhlas na nejnovější změny operačního systému tak, že přidáte soubor app.manifest v testovací aplikaci a zrušení komentář Windows 10 nepodporuje řádku operačního systému, aby vypadal jako následující:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Některé příklady vysoký kontrast změny patří:

- Značky zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.

- Pokud vybraná, zakázané <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.

- Text ve vybrané <xref:System.Windows.Forms.Button> řízení totéž co barva výběru.

- Zakázaný text je snadnější čtení. Příklad:

    Před:

    ![Zakázaný text před vylepšení přístupnosti](media/wf-disabled-before.png) 

    Po:

    ![Zakázaný text po vylepšení přístupnosti](media/wf-disabled-after.png) 

- Vysoký kontrast vylepšení v dialogovém okně výjimka přístup z více vláken.

**Vylepšená podpora Předčítání**

Windows Forms v rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro předčítání:

- <xref:System.Windows.Forms.MonthCalendar> Ovládací prvek je přístupná Předčítání, a také v jiných nástrojích automatizace uživatelského rozhraní.

- <xref:System.Windows.Forms.CheckedListBox> Řízení upozorní Předčítání při změně stavu zkontrolujte položky tak, že se uživateli upozornění, že jste změněna hodnota položky seznamu.
 
- <xref:System.Windows.Forms.DataGridViewCell> Řízení sestavy Předčítání správný stav jen pro čtení.
 
- Program Předčítání může načíst zakázáno <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dříve by přeskočit položky nabídky zakázané.

**Vylepšená podpora pro usnadnění vzory vlastnosti UIAutomation**

Od verze rozhraní .NET Framework 4.7.1, vývojáři nástrojů technologie usnadnění, můžou využít běžných vzorů usnadnění rozhraní API a vlastností pro ovládací prvky několik WinForms. Usnadnění vylepšení patří:

- <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> teď podporují [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Teď podporuje [přepnutí vzor](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- <xref:System.Windows.Forms.ToolStripItem> Podporuje ovládací prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> podporu ovládací prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.

**Práce s prohlížečem vylepšené vlastnost**

Od verze rozhraní .NET Framework 4.7.1, Windows Forms zahrnuje:

- Lepší navigační klávesnice prostřednictvím různých windows rozevíracího seznamu výběru.
- Snížení nepotřebné zarážek tabulátoru.
- Typy ovládacích prvků hlášení lépe.
- Vylepšené Předčítání chování.
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a>Ovládací prvky ASP.NET web

Od verze rozhraní .NET Framework 4.7.1 a Visual Studio 2017 15.3, ASP.NET zvyšuje, jak fungují ovládacích prvků ASP.NET pomocí technologie usnadnění v sadě Visual Studio. Změny zahrnují následující:

- Změny implementace chybějící vzorů usnadnění uživatelského rozhraní v ovládacích prvcích, jako je třeba **přidat pole** dialogové okno ve **zobrazení podrobností o** průvodce, nebo **Konfigurovat ListView** dialogovém **ListView** průvodce.

- Změny ke zlepšení zobrazení v režimu vysokého kontrastu, jako je třeba **editoru služby Data Pager pole**.

- Změny ke zlepšení navigační klávesnice vyskytne pro ovládací prvky, jako je třeba **pole** dialogové okno ve **upravit pole stránkování** Průvodce prvku DataPager **ObjectContext konfigurace**  dialogové okno, nebo **Konfigurovat výběr dat** dialogovém **konfigurace zdroje dat** průvodce.

<a name="tools471"></a>
## <a name="net-sdk-tools"></a>.NET SDK – nástroje

[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) došlo k vylepšení opravou rozmanitých problémy. Většina z nich byly drobných záležitostí, jako je název není definované nebo určité vzorce automatizace uživatelského rozhraní není implementovaná správně. Zatímco mnoho uživatelé nebudou vědět nesprávné hodnoty, zákazníkům, kteří používají technologie pro usnadnění jako čtečky obrazovky zjistí tyto sady SDK nástroje přístup. 

Tato vylepšení změnit některé předchozí chování, například pořadí fokus klávesnice.

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a>Návrhář Windows Workflow Foundation (WF) pracovního postupu

Usnadnění změny v Návrháři pracovních postupů, patří:

- Pořadí karet se změní na zleva doprava a shora dolů v některé ovládací prvky:

  - Okno inicializovat korelace pro nastavení korelace dat pro <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.

  - Okno obsahu definice pro <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity.

- Další funkce jsou dostupné prostřednictvím klávesnice:

  - Při úpravě vlastností aktivity, vlastnost skupiny lze sbalit pomocí klávesnice poprvé, které se zaměřuje.

  - Ikony upozornění jsou přístupné pomocí klávesnice.

  - **Více vlastnosti** v tlačítko **vlastnosti** okno je přístupná pomocí klávesnice.

  - Klávesnice mohou uživatelé položky hlavičky v **argumenty** a **proměnné** podokna Návrháře pracovních postupů.

- Lepší viditelnost položek s fokusem, jako např. kdy:

  - Přidání řádků do datových mřížek používají návrháři návrháře pracovních postupů a aktivit.

  - Stisknutím klávesy tabulátor procházíte polí v <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity.

  - Nastavení výchozí hodnoty pro proměnné nebo argumenty

- Nyní můžete správné rozpoznání čtečky obrazovky:

  - Nastavte zarážky v Návrháři pracovních postupů.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, A <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.
  - Obsah <xref:System.ServiceModel.Activities.Receive> aktivity.

  - Cílový typ <xref:System.Activities.Statements.InvokeMethod> aktivity.

  - Pole se seznamem výjimky a nakonec v části <xref:System.Activities.Statements.TryCatch> aktivity.

  - Pole se seznamem typ zprávy, rozdělovače v okně Přidat inicializátory korelace, okno obsahu definice a definice CorrelatesOn okno v zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Stav počítač přejde a přejde cíle.

  - Poznámky a konektory na <xref:System.Activities.Statements.FlowDecision> aktivity.

  - Kontextové (klikněte pravým tlačítkem) nabídky pro aktivity.

  - Editory hodnotu vlastnosti, na tlačítko Vymazat vyhledat, podle kategorie a abecedním řazení tlačítek a dialogové okno Editor výraz ve vlastnosti mřížky.

  - Procento přiblížení v Návrháři pracovních postupů.

  - Oddělovač v <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.

  - <xref:System.Activities.Statements.InvokeDelegate> Aktivity.

  - Vyberte typy okna pro slovník aktivity (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`atd.).

  - Okno Procházet a vyberte typ formátu .NET.

  - Popis cesty v Návrháři pracovních postupů.

- Řady vylepšení v viditelnost návrháře pracovních postupů a jeho ovládacích prvků, jako je lepší kontrast poměr mezi elementy a použít pro prvky výběru výraznější výběr polí se zobrazí uživatelům, kteří se rozhodnou vysoký kontrast motivů.

## <a name="see-also"></a>Viz také

[Co je nového v rozhraní .NET Framework](whats-new.md)
 
