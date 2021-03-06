---
title: Co je nového v přístupnosti v .NET Framework
description: Podívejte se, co je nového v přístupnost .NET, počínaje .NET Framework 4.7.1. Funkce usnadnění umožňují, aby aplikace poskytovala správné prostředí pro uživatele s asistenčními technologiemi.
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: df9188c4f7c2af77f5dc87309880a41724254c5c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558956"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Co je nového v přístupnosti v .NET Framework

.NET Framework se zaměřuje na zajištění přístupnosti aplikací pro vaše uživatele. Funkce usnadnění umožňují aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění. Počínaje .NET Framework 4.7.1 .NET Framework obsahuje velký počet vylepšení usnadnění, která vývojářům umožňují vytvářet přístupné aplikace.

## <a name="accessibility-switches"></a>Přepínače přístupnosti

Aplikaci můžete nakonfigurovat tak, aby se přihlásila k funkcím přístupnosti, pokud cílíte .NET Framework 4,7 nebo starší verzi, ale běží na .NET Framework 4.7.1 nebo novějším. Pokud cílíte .NET Framework 4.7.1 nebo novější, můžete aplikaci nakonfigurovat tak, aby používala starší funkce (a nevyužila výhody funkcí usnadnění). Každá verze .NET Framework, která zahrnuje funkce usnadnění, má přepínač dostupnosti specifický pro verzi, který přidáte do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace. Podporovány jsou následující přepínače:

|Verze|Přepínač|
|---|---|
|.NET Framework 4.7.1|"Switch. UseLegacyAccessibilityFeatures"|
| .NET Framework 4.7.2|"Switch. UseLegacyAccessibilityFeatures. 2"|
| .NET Framework 4.8|"Switch. UseLegacyAccessibilityFeatures. 3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Využití výhod vylepšení usnadnění přístupu

Nové funkce usnadnění jsou ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4.7.1 nebo novější. Kromě toho aplikace, které cílí na starší verzi .NET Framework, ale jsou spuštěné v .NET Framework 4.7.1 nebo novější, se mohou odhlásit ze starší verze chování přístupnosti (a tím využít výhod vylepšení usnadnění) přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace a nastavením jejich hodnoty na `false` . V následující části se dozvíte, jak se vyjádřit k vylepšením usnadnění zavedeným v .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Pokud se rozhodnete pro funkce přístupnosti v novější verzi .NET Framework vyjádřit, musíte se taky výslovně odhlásit k funkcím z dřívějších verzí .NET Framework. Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1 i 4.7.2 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1, 4.7.2 a 4,8 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Obnovení starší verze chování

Aplikace, které cílí na verze .NET Framework začínající na 4.7.1, mohou zakázat funkce usnadnění přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace a nastavením jejich hodnoty na `true` . Například následující konfigurace výslovný z funkcí usnadnění zavedených v .NET Framework 4.7.2:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>Co je nového v přístupnosti v .NET Framework 4,8

.NET Framework 4,8 obsahuje nové funkce pro usnadnění přístupu v následujících oblastech:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)](#wf48)

<a name="winforms48"></a>

### <a name="windows-forms"></a>Windows Forms

V .NET Framework 4,8 model Windows Forms přidává podporu pro události LiveRegions a Notification k mnoha běžně používaným ovládacím prvkům. Pokud uživatel přejde k ovládacímu prvku pomocí klávesnice, přidá také podporu pro popisky tlačítek.

**Podpora UIA LiveRegions ve jmenovkách a StatusStrips**

UIA LiveRegions umožňuje vývojářům aplikací upozorňovat čtečky obrazovky na změnu textu v ovládacím prvku, který se nachází vedle místa, kde uživatel pracuje. To je užitečné například pro <xref:System.Windows.Forms.StatusStrip> ovládací prvek, který zobrazuje stav připojení. Pokud se připojení vynechá a změní se stav, vývojář může chtít informovat čtečku obrazovky.

Počínaje .NET Framework 4,8 model Windows Forms implementuje UIA LiveRegions pro <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> ovládací prvky a. Například následující kód používá LiveRegion v <xref:System.Windows.Forms.Label> ovládacím prvku s názvem `label1` :

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Narrator oznamuje "připravený" bez ohledu na to, kde uživatel interakci s aplikací.

Můžete také implementovat <xref:System.Windows.Forms.UserControl> jako LiveRegion:

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

**Události oznámení UIA**

Událost oznámení UIA zavedená ve Windows 10 vede k aktualizaci Creators Update, umožňuje vaší aplikaci vyvolat událost UIA, která vede k tomu, že v programu Narrator stačí vytvořit oznámení na základě textu, který zadáte do události, aniž by bylo nutné mít odpovídající ovládací prvek v uživatelském rozhraní. V některých scénářích je to jednoduchý způsob, jak výrazně zlepšit přístupnost vaší aplikace. Aplikace může být užitečná také pro oznamování průběhu některých procesů, které mohou trvat dlouhou dobu. Další informace o událostech oznámení UIA najdete v tématu [může vaše desktopová aplikace využít novou událost oznámení uživatelského rozhraní?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).

Následující příklad vyvolá [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Popisy tlačítek při přístupu k klávesnicím**

V aplikacích, které cílí na .NET Framework 4.7.2 a starších verzí, lze [Popis](xref:System.Windows.Forms.ToolTip) ovládacího prvku aktivovat pouze přesunutím ukazatele myši do ovládacího prvku. Počínaje .NET Framework 4,8 může uživatel klávesnice aktivovat Popis ovládacího prvku tím, že zaměří ovládací prvek pomocí klávesy tabulátoru nebo kláves se šipkami s nebo bez modifikačních kláves. Toto konkrétní vylepšení přístupnosti vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

Následující obrázek znázorňuje popis tlačítka, když uživatel vybere tlačítko s klávesnicí.

![Snímek obrazovky s popisem, když uživatel přejde na tlačítko s klávesnicí](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Počínaje .NET Framework 4,8, WPF zahrnuje řadu vylepšení usnadnění.

**Narrator obrazovky již neoznamuje prvky se sbalenou nebo skrytou viditelností**

Prvky se sbalenou nebo skrytou viditelností již nejsou oznamovány čtečkou obrazovky. Uživatelská rozhraní, která obsahují prvky s viditelností <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> mohou být reprezentována čtečkami obrazovky, pokud jsou uživateli oznámena. Počínaje .NET Framework 4,8, WPF již nezahrnuje sbalené nebo skryté prvky v zobrazení ovládacích prvků stromu UIAutomation, takže čtečky obrazovky již nemohou tyto prvky oznamovat.

**Vlastnost SelectionTextBrush, která se má použít pro výběr textu, který není založený na Doplňky**

V .NET Framework 4.7.2 WPF přidala možnost kreslit <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> vybírat text bez použití přípravné vrstvy. Barva popředí vybraného textu v tomto scénáři byla vyřízena nástrojem <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> .

.NET Framework 4,8 přidá novou vlastnost, `SelectionTextBrush` která umožňuje vývojářům vybrat konkrétní štětec pro vybraný text při použití bez vizuálního výběru textu. Tato vlastnost funguje pouze na <xref:System.Windows.Controls.Primitives.TextBoxBase> odvozených ovládacích prvcích a <xref:System.Windows.Controls.PasswordBox> ovládacím prvku v aplikacích WPF, které mají povolený výběr textu založený na nedoplňky. Nefunguje na <xref:System.Windows.Controls.RichTextBox> ovládacím prvku. Pokud není povolený výběr textu založený na doplňku, bude tato vlastnost ignorována.

Chcete-li použít tuto vlastnost, jednoduše ji přidejte do kódu XAML a použijte příslušný štětec nebo vazbu. Výsledný výběr textu vypadá takto:

![Snímek obrazovky aplikace se spuštěnými slovy Hello World vybraných.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

Můžete zkombinovat použití `SelectionBrush` `SelectionTextBrush` vlastností a k vygenerování libovolné kombinace barev pozadí a popředí, kterou považujete za vhodnou.

**Podpora pro vlastnost UIAutomation ControllerFor**

Vlastnost UIAutomation `ControllerFor` vrací pole prvků automatizace, které jsou manipulovány prvkem automatizace, který tuto vlastnost podporuje. Tato vlastnost se běžně používá pro usnadnění přístupu k automatickým návrhům. `ControllerFor` se používá v případě, že prvek automatizace ovlivňuje jeden nebo více segmentů uživatelského rozhraní aplikace nebo plochy. V opačném případě je těžké přidružit dopad operace řízení k prvkům uživatelského rozhraní. Tato funkce přidává možnost pro ovládací prvky pro poskytnutí hodnoty `ControllerFor` Vlastnosti.

.NET Framework 4,8 přidá novou virtuální metodu <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType> . Chcete-li zadat hodnotu `ControllerFor` vlastnosti, jednoduše přepište tuto metodu a vraťte se `List<AutomationPeer>` k ovládacím prvkům, které jsou zpracovávány tímto <xref:System.Windows.Automation.Peers.AutomationPeer> způsobem:

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

**Popisy tlačítek při přístupu k klávesnicím**

V .NET Framework 4.7.2 a starších verzích se popisy tlačítek zobrazují pouze v případě, že uživatel najede myší na ovládací prvek. V .NET Framework 4,8 se popisy tlačítek zobrazují také u fokusu klávesnice a také prostřednictvím klávesové zkratky.

Chcete-li povolit tuto funkci, aplikace musí cílit .NET Framework 4,8 nebo se přihlásit pomocí `Switch.UseLegacyAccessibilityFeatures.3` `Switch.UseLegacyToolTipDisplay` přepínačů a [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) . Následuje ukázkový konfigurační soubor aplikace:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

Jakmile je tato možnost povolená, všechny ovládací prvky, které obsahují popisek, ji zobrazí, jakmile ovládací prvek dostane fokus klávesnice. Popis tlačítka může být v průběhu času zavřen nebo se změní fokus klávesnice. Uživatelé mohou popisek také zavřít ručně pomocí nové klávesové zkratky CTRL + SHIFT + F10. Po odvolání ovládacího prvku ToolTip se můžete znovu zobrazit pomocí stejné klávesové zkratky.

> [!NOTE]
> [Popisky pásu karet](xref:System.Windows.Controls.Ribbon.RibbonToolTip) u <xref:System.Windows.Controls.Ribbon.Ribbon> ovládacích prvků se nezobrazují na fokusu klávesnice. zobrazují se pouze prostřednictvím klávesové zkratky.

**Přidaná podpora vlastností SizeOfSet a PositionInSet UIAutomation**

Windows 10 představil dvě nové vlastnosti UIAutomation `SizeOfSet` a `PositionInSet` , které aplikace používají k popisu počtu položek v sadě. UIAutomation klientské aplikace, jako jsou čtečky obrazovky, pak mohou pro tyto vlastnosti zadat dotaz na aplikaci a oznámit přesnou reprezentaci uživatelského rozhraní aplikace.

Počínaje .NET Framework 4,8, WPF zpřístupňuje tyto dvě vlastnosti UIAutomation v aplikacích WPF. Toho lze dosáhnout dvěma způsoby:

- Pomocí vlastností závislosti.

  WPF přidává dvě nové vlastnosti závislosti <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType> . Vývojář může použít jazyk XAML k nastavení jejich hodnot:

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- Přepsáním virtuálních metod AutomationPeer.

  <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> Virtuální metody a byly přidány do třídy AutomationPeer. Vývojář může poskytnout hodnoty pro `SizeOfSet` a `PositionInSet` přepsáním těchto metod, jak je znázorněno v následujícím příkladu:

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

Kromě toho položky v <xref:System.Windows.Controls.ItemsControl> instancích poskytují hodnotu pro tyto vlastnosti automaticky bez dalšího zásahu od vývojáře. Pokud <xref:System.Windows.Controls.ItemsControl> je seskupená, kolekce skupin se reprezentuje jako sada a každá skupina se počítá jako samostatná sada, přičemž každá položka v této skupině poskytuje polohu v této skupině a také velikost skupiny. Automatické hodnoty nejsou virtualizací ovlivněny. I v případě, že položka není vytvořena, je stále započítána do celkové velikosti sady a má vliv na pozici v sadě položek na stejné úrovni.

Automatické hodnoty jsou poskytnuty pouze v případě, že aplikace cílí na .NET Framework 4,8. Pro aplikace, které cílí na starší verzi .NET Framework, můžete nastavit `Switch.UseLegacyAccessibilityFeatures.3` [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App.config:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)

Návrhář pracovního postupu obsahuje následující změny v .NET Framework 4,8:

- Uživatelům, kteří používají program Narrator, se zobrazí vylepšení popisků případu FlowSwitch.

- Uživatelům, kteří používají program Narrator, se v popisech tlačítek zobrazí vylepšení.

- Uživatelům, kteří si zvolí Vysoký kontrast motivům, se budou zobrazovat vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako jsou lepší poměry kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.

Pokud je vaše aplikace cílena .NET Framework 4.7.2 nebo starší verze, můžete tyto změny vyjádřit nastavením `Switch.UseLegacyAccessibilityFeatures.3` [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na `false` v konfiguračním souboru aplikace. Další informace najdete v části využití [vylepšení usnadnění](#taking-advantage-of-accessibility-enhancements) v tomto článku.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>Co je nového v přístupnosti v .NET Framework 4.7.2

.NET Framework 4.7.2 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Barvy definované operačním systémem v motivech Vysoký kontrast**

Počínaje .NET Framework 4.7.2 model Windows Forms používá v Vysoký kontrast motivech barvy definované operačním systémem. To má vliv na následující ovládací prvky:

- Rozevírací šipka <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku

- <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavením na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> . Dříve byly barvy vybraného textu a pozadí nekontrastované a bylo těžké je přečíst.

- Ovládací prvky obsažené v rámci <xref:System.Windows.Forms.GroupBox> , které mají svou <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na `false` .

- <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> Ovládací prvky, a, <xref:System.Windows.Forms.ToolStripDropDownButton> které mají vyšší poměr kontrastu světelnosti v režimu Vysoký kontrast.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor>Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell> .

**Vylepšení Předčítání**

Počínaje .NET Framework 4.7.2 se podpora Narrator rozšiřuje takto:

- Oznamuje hodnotu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> vlastnosti při oznamování textu <xref:System.Windows.Forms.ToolStripMenuItem> .

- Indikuje, že <xref:System.Windows.Forms.ToolStripMenuItem> má <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na `false` .

- Pokud <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je vlastnost nastavena na hodnotu, poskytuje zpětnou vazbu ke stavu zaškrtávacího políčka `true` .

- Pořadí fokusu v režimu kontroly mluveného komentáře je konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně Stažení ClickOnce.

**Vylepšení ovládacího prvku DataGridView**

Počínaje .NET Framework 4.7.2 <xref:System.Windows.Forms.DataGridView> zavedl ovládací prvek následující vylepšení přístupnosti:

- Řádky lze seřadit pomocí klávesnice. Uživatel může použít klávesu F3, aby bylo možné řadit podle aktuálního sloupce.

- Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , změní se barva záhlaví sloupce tak, aby označovala aktuální sloupec jako karty uživatelů na aktuálním řádku.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType>Vlastnost objektu <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správný nadřazený ovládací prvek.

**Vylepšené vizuální pomůcky**

- <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastností zobrazují indikátor fokusu, když obdrží fokus.

**Vylepšená podpora mřížky vlastností**

- <xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku nyní vrátí `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pro vlastnost pouze v případě, že je povolen prvek PropertyGrid.

- <xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku vrátí `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost pro vlastnost pouze v případě, že uživatel může změnit element PropertyGrid.

**Vylepšená navigace klávesnicí**

- <xref:System.Windows.Forms.ToolStripButton>Ovládací prvek umožňuje fokus, pokud je obsažen v typu <xref:System.Windows.Forms.ToolStripPanel> , který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavenou na hodnotu`true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Změny ovládacích prvků CheckBox a RadioButton**

V .NET Framework 4.7.1 a starších verzích <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> mají WPF a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> Controls nekonzistentní a v klasických a vysoký kontrast motivech nesprávné vizuály fokusu.  K těmto problémům dochází v případech, kdy ovládací prvky nemají sadu obsahu.  To může zjednodušit přechod mezi motivy a označit vizuál jako fokus.

V .NET Framework 4.7.2 jsou teď tyto vizuály v různých motivech konzistentní a snadněji viditelné v klasických a Vysoký kontrastch motivech.

**Ovládací prvky WinForms hostované v aplikaci WPF**

Pro ovládací prvek WinForms, který je hostován v aplikaci WPF v .NET Framework 4.7.1 a starších verzích, uživatelé nemohli kartu vymezit vrstvy WinForms, pokud je první nebo poslední ovládací prvek v této vrstvě <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvkem WPF. V .NET Framework 4.7.2 uživatelé teď můžou z vrstvy WinForms vymezit kartu.

Automatizované aplikace, které spoléhají na fokus bez použití řídicího panelu Vrstvy WinForms, ale nemusí nadále fungovat podle očekávání.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>Co je nového v přístupnosti v .NET Framework 4.7.1

.NET Framework 4.7.1 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [Webové ovládací prvky ASP.NET](#aspnet471)

- [SDK Tools .NET](#tools471)

- [Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Vylepšení čtečky obrazovky**

Pokud jsou povolena vylepšení přístupnosti, .NET Framework 4.7.1 zahrnuje následující vylepšení, která ovlivňují čtečky obrazovky:

- V .NET Framework 4,7 a starších verzích <xref:System.Windows.Controls.Expander> byly ovládací prvky oznámeny čtečkami obrazovky jako tlačítka. Počínaje .NET Framework 4.7.1 jsou správně ohlášeny jako rozbalitelné nebo Sbalitelné skupiny.

- V .NET Framework 4,7 a dřívějších verzích <xref:System.Windows.Controls.DataGridCell> byly ovládací prvky oznámeny čtečkami obrazovky jako "vlastní". Počínaje .NET Framework 4.7.1 jsou teď správně ohlášené jako buňka datové mřížky (lokalizovaná).

- Počínaje .NET Framework 4.7.1, čtečky obrazovky oznamují název, který lze upravovat <xref:System.Windows.Controls.ComboBox> .

- V .NET Framework 4,7 a dřívějších verzích <xref:System.Windows.Controls.PasswordBox> byly ovládací prvky oznámeny jako "žádná položka v zobrazení" nebo jinak nesprávnému chování. Tento problém je vyřešený od .NET Framework 4.7.1.

**Podpora UIAutomation LiveRegion**

Čtečky obrazovky, jako je Narrator, usnadňují uživatelům čtení obsahu uživatelského rozhraní aplikace, obvykle výstupem z textu na řeč, který má fokus. Pokud se však prvek uživatelského rozhraní změní a nemá fokus, uživatel nemusí být upozorněn a může si vyvšimnout důležitých informací. Při řešení tohoto problému se zaměřují na živé oblasti. Vývojář je může použít k informování čtečky obrazovky nebo jakéhokoliv jiného klienta UIAutomation, že došlo k důležité změně v prvku uživatelského rozhraní. Čtečka obrazovky pak může rozhodnout, jak a kdy se má uživatel informovat o této změně.

V rámci podpory živých oblastí byla do WPF přidána následující rozhraní API:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>Pole a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> , která identifikují vlastnost **LiveSetting** a událost **LiveRegionChanged** . Lze je nastavit pomocí jazyka XAML.

- Připojená vlastnost **Vlastnosti automatizace. LiveSetting** , která informuje čtečku obrazovky o důležitosti změny uživatelského rozhraní pro uživatele.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>Vlastnost, která identifikuje vlastnost **Vlastnosti automatizace. LiveSetting** připojené.

- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>Metoda, která může být přepsána tak, aby poskytovala hodnotu **LiveSetting** .

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>Metody a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , které získají a nastavují hodnotu **LiveSetting** .

- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>Výčet, který definuje následující možné hodnoty **LiveSetting** :

  - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Element neodesílá oznámení v případě, že se změnil obsah oblasti v reálném čase.
  - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Element odesílá nepřerušovaná oznámení, pokud se změní obsah živé oblasti.

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Element odesílá oznámení o přerušování, pokud se změní obsah živé oblasti.

LiveRegion můžete vytvořit nastavením vlastnosti **Vlastnosti automatizace. LiveSetting** u elementu Interest, jak je znázorněno v následujícím příkladu:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Když se data v živé oblasti změní a potřebujete informovat čtečku obrazovky, explicitně vyvoláte událost, jak je znázorněno v následující ukázce.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**High contrast**

Počínaje .NET Framework 4.7.1 se v různých ovládacích prvcích WPF provedla vylepšení vysokého kontrastu. Jsou nyní viditelné, když <xref:System.Windows.SystemParameters.HighContrast%2A> je motiv nastaven. Tady jsou některé z nich:

- <xref:System.Windows.Controls.Expander> nad

  Vizuál fokusu pro  <xref:System.Windows.Controls.Expander> ovládací prvek je nyní viditelný. Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.RadioButton> ovládací prvky, a jsou viditelné také. Příklad:

  Před:

  ![Snímek obrazovky ovládacího prvku rozšíření s fokusem a bez vizuálu fokusu](./media/whats-new-in-accessibility/expander-control-before.png)

  Po:

  ![Snímek obrazovky ovládacího prvku rozšíření se fokusem ukazující tečkovou čáru kolem textu ovládacího prvku](./media/whats-new-in-accessibility/expander-control-after.png)

- <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky

  Text v <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> ovládacích prvcích a se teď snáze zobrazuje, když je vybraný v motivech s vysokým kontrastem. Příklad:

  Před:

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s nekvalitní viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  Po:

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s lepší viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> nad

  Počínaje .NET Framework 4.7.1 je ohraničení zakázaného <xref:System.Windows.Controls.ComboBox> ovládacího prvku stejné barvy jako zakázaný text. Příklad:

  Před:

  ![Snímek obrazovky zakázaného pole se seznamem s textem ohraničení a ovládacího prvku v různých barvách](./media/whats-new-in-accessibility/combo-disabled-before.png)

  Po:

  ![Snímek obrazovky zakázaného pole se seznamem s ohraničením stejné barvy jako text ovládacího prvku](./media/whats-new-in-accessibility/combo-disabled-after.png)

  Kromě toho zakázaná a zaměřená tlačítka používají správnou barvu motivu.

  Před:

  ![Snímek obrazovky černého tlačítka se šedým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  Po:

  ![Snímek obrazovky s modrým tlačítkem s černým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  Nakonec v .NET Framework 4,7 a starších verzích nastaví <xref:System.Windows.Controls.ComboBox> styl ovládacího prvku na hodnotu `Toolbar.ComboBoxStyleKey` neviditelná šipka rozevíracího seznamu. Tento problém je vyřešený od .NET Framework 4.7.1. Příklad:

  Před:

  ![Snímek obrazovky ovládacího prvku ComboBox se skrytou šipkou rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  Po:

  ![Snímek obrazovky ovládacího prvku polem, který zobrazuje šipku rozevíracího seznamu.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <xref:System.Windows.Controls.DataGrid> nad

  Počínaje .NET Framework 4.7.1, šipka indikátoru řazení v <xref:System.Windows.Controls.DataGrid> ovládacích prvcích teď používá správné barvy motivu. Příklad:

  Před:

  ![Snímek obrazovky se šipkou indikátoru řazení před vylepšeními](./media/whats-new-in-accessibility/sort-indicator-before.png)

  Po:

  ![Snímek obrazovky se šipkou indikátoru řazení po vylepšeních](./media/whats-new-in-accessibility/sort-indicator-after.png)

  Kromě toho se v .NET Framework 4,7 a dřívějších verzích změnil výchozí styl propojení na nesprávnou barvu při stisknutí myši v režimech s vysokým kontrastem. Tento problém se vyřeší od .NET Framework 4.7.1. Podobně, <xref:System.Windows.Controls.DataGrid> sloupce Zaškrtávací políčko používá očekávané barvy zpětné vazby pro fokus klávesnice počínaje .NET Framework 4.7.1.

  Před:

  ![Snímek obrazovky s odkazem na něj klikněte červeně.](./media/whats-new-in-accessibility/default-link-style-before.png)

  Po:

  ![Snímek obrazovky s odkazem na něj klikněte žlutě.](./media/whats-new-in-accessibility/default-link-style-after.png)

Další informace o vylepšení usnadnění přístupu WPF v .NET Framework 4.7.1 najdete v tématu [vylepšení usnadnění v WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Vylepšení model Windows Forms dostupnosti

V .NET Framework 4.7.1, model Windows Forms (WinForms), zahrnuje změny přístupnosti v následujících oblastech.

**Vylepšené zobrazení v režimu Vysoký kontrast**

Počínaje .NET Framework 4.7.1 různé ovládací prvky WinForms nabízejí Vylepšené vykreslování v režimech HighContrast, které jsou k dispozici v operačním systému. Windows 10 změnil hodnoty pro některé systémové barvy s vysokým kontrastem a model Windows Forms vychází z rozhraní Win32 pro Windows 10. Pro dosažení co nejlepších výsledků spusťte aplikaci v nejnovější verzi Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru App. manifest do testovací aplikace a odkomentujte podporovanou řádku operačního systému Windows 10 tak, aby vypadala takto:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

Mezi tyto změny vysokého kontrastu patří:

- Zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položkách je snazší zobrazit.

- Je-li toto políčko zaškrtnuto, <xref:System.Windows.Forms.MenuStrip> je snazší zobrazit zakázané položky.

- Text ve vybraném <xref:System.Windows.Forms.Button> ovládacím prvku má kontrast na barvě výběru.

- Nepovolený text je snazší číst. Příklad:

  Před:

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem před vylepšeními přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  Po:

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem po vylepšeních přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- Vylepšení vysokého kontrastu v dialogovém okně výjimky vlákna.

**Vylepšená podpora Narrator**

Model Windows Forms v .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro program Narrator:

- K <xref:System.Windows.Forms.MonthCalendar> ovládacímu prvku může přicházet program Narrator a také k ostatním nástrojům pro automatizaci uživatelského rozhraní.

- <xref:System.Windows.Forms.CheckedListBox>Ovládací prvek upozorní program Narrator, když se změní stav kontroly položky, takže uživatel bude informován o tom, že změnil hodnotu položky seznamu.

- <xref:System.Windows.Forms.DataGridViewCell>Ovládací prvek oznamuje do programu Narrator správný stav jen pro čtení.

- Program Narrator teď může číst zakázaný <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dřív by přeskočil zakázané položky nabídky.

**Vylepšená podpora pro vzory usnadnění UIAutomation**

Od .NET Framework 4.7.1 můžou vývojáři nástrojů pro usnadnění přístupu využít běžné vzory a vlastnosti přístupnosti rozhraní API pro několik ovládacích prvků WinForms. Mezi tato vylepšení přístupnosti patří:

- <xref:System.Windows.Forms.ComboBox>A <xref:System.Windows.Forms.ToolStripSplitButton> teď podporuje [model rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>Teď podporuje [vzor přepínacího](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)tlačítka.

- <xref:System.Windows.Forms.ToolStripItem>Ovládací prvek podporuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a vzorek pro [rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> Ovládací prvky a podporují <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.

**Vylepšené prostředí prohlížeče vlastností**

Počínaje .NET Framework 4.7.1 model Windows Forms zahrnuje:

- Lepší navigace pomocí klávesnice v různých oknech pro výběr rozevíracího seznamu.
- Snížení zbytečných zarážek tabulátoru.
- Lepší vytváření sestav typů ovládacích prvků.
- Vylepšené chování Předčítání.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>Webové ovládací prvky ASP.NET

Počínaje .NET Framework 4.7.1 a sadou Visual Studio 2017 verze 15,3 ASP.NET vylepšuje, jak ASP.NET webové ovládací prvky fungují s technologiemi usnadnění v aplikaci Visual Studio. Změny zahrnují následující:

- Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno **Přidat pole** v průvodci **zobrazení podrobností** nebo dialogové okno **Konfigurovat ListView** průvodce **ListView** .

- Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například **Editor polí datového pageru**.

- Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno **pole** v průvodci **úpravou polí stránkování** ovládacího prvku DataPager, dialogové **okno Konfigurovat ObjectContext** nebo dialogové okno **Konfigurovat výběr dat** v průvodci **konfigurací zdroje dat** .

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>SDK Tools .NET

[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých problémů s přístupností. Většina těchto došlo k malým problémům, jako je název, který není definován, nebo některé vzorce automatizace uživatelského rozhraní nejsou správně implementovány. I když mnoho uživatelů nebude vědět o těchto nesprávných hodnotách, zákazníci, kteří používají asistenční technologie, jako jsou čtečky obrazovky, budou tyto nástroje sady SDK k dispozici podrobněji.

Tato vylepšení mění některá předchozí chování, jako je například pořadí fokusu klávesnice.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění

Změny přístupnosti v Návrhář postupu provádění zahrnují následující:

- Pořadí karet se změní na zleva doprava a shora dolů v některých ovládacích prvcích:

  - Okno Inicializace korelace pro nastavení dat korelace pro <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu.

  - Okno Definice obsahu pro <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> aktivity,, a <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> .

- Další funkce jsou k dispozici prostřednictvím klávesnice:

  - Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny klávesnicí při prvním zaměření.

  - Ikony upozornění jsou přístupné z klávesnice.

  - Tlačítko **Další vlastnosti** v okně **vlastnosti** je přístupné z klávesnice.

  - Uživatelé klávesnice mají přístup k položkám záhlaví v podoknech **argumenty** a **proměnné** Návrhář postupu provádění.

- Vylepšená viditelnost položek s fokusem, například když:

  - Přidávání řádků do datových mříží používaných návrháři Návrhář postupu provádění a aktivit.

  - Procházení polí v <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> aktivitách a

  - Nastavení výchozích hodnot pro proměnné nebo argumenty

- Čtečky obrazovky teď můžou správně rozpoznat:

  - Zarážky nastavené v Návrháři postupu.

  - <xref:System.Activities.Statements.FlowSwitch%601>Aktivity, <xref:System.Activities.Statements.FlowDecision> a <xref:System.ServiceModel.Activities.CorrelationScope> .
  - Obsah <xref:System.ServiceModel.Activities.Receive> aktivity

  - Cílový typ <xref:System.Activities.Statements.InvokeMethod> aktivity.

  - Pole se seznamem výjimek a oddíl finally v <xref:System.Activities.Statements.TryCatch> aktivitě.

  - Pole se seznamem typ zprávy, rozdělovač v okně Přidat Inicializátory korelace, okno Definice obsahu a okno definice vlastnosti CorrelatesOn v aktivitách zasílání zpráv ( <xref:System.ServiceModel.Activities.Receive> ,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> ).

  - Cíle přechodů a přechodů stavového stroje.

  - Poznámky a konektory v <xref:System.Activities.Statements.FlowDecision> aktivitách.

  - Místní nabídky pro aktivity v kontextu (klikněte pravým tlačítkem myši).

  - Editor hodnot vlastností, tlačítko Vymazat hledání, kategorie podle abecedy a abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.

  - Procento přiblížení v Návrhář postupu provádění.

  - Oddělovač v rámci <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.

  - <xref:System.Activities.Statements.InvokeDelegate>Aktivita.

  - Okno vybrat typy pro aktivity slovníku ( `Microsoft.Activities.AddToDictionary<TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` atd.).

  - Okno Procházet a vybrat typ .NET.

  - Popis cesty v Návrhář postupu provádění.

- Uživatelům, kteří si zvolí Vysoký kontrast Themes, se zobrazí mnoho vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako je lepší poměr kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.

## <a name="see-also"></a>Viz také

- [Novinky v rozhraní .NET Framework](index.md)
