---
title: "Co je nového v usnadnění v rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f17550bc0cc4919f00dc93c8e92d258b38c4f76
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Co je nového v usnadnění v rozhraní .NET Framework

Rozhraní .NET Framework se zaměřuje na provedení další accessibile pro vaše uživatele aplikace. Funkce usnadnění povolit aplikace a poskytuje příslušné prostředí pro uživatele technologie usnadnění. Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupná. 

Nové funkce pro usnadnění přístupu jsou povolené ve výchozím nastavení pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější. Kromě toho aplikace, které cílení na dřívější verzi rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 a později se můžete rozhodnout ze starší verze usnadnění chování (a tím vyjádřit výslovný souhlas k vylepšení přístupnosti v rozhraní .NET Framework 4.7.1) podle Přidání následující přepínač tak, aby [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Podobně můžete zakázat funkce usnadnění přidáním následující přepínač tak, aby aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7.1 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 zahrnuje nové funkce usnadnění v těchto oblastech:

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

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
 
## <a name="see-also"></a>Viz také
[Co je nového v rozhraní .NET Framework](whats-new.md)   
 
