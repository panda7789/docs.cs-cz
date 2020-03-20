---
title: Co je nového v usnadnění v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4dbc2024aa2e956b23030ae6eab987e65e006d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400181"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Co je nového v usnadnění v rozhraní .NET Framework

Rozhraní .NET Framework má za cíl zpřístupnit aplikace uživatelům. Funkce usnadnění umožňují aplikaci poskytovat uživatelům asistenční technologie odpovídající prostředí. Počínaje rozhraním .NET Framework 4.7.1 obsahuje rozhraní .NET Framework velké množství vylepšení usnadnění, která vývojářům umožňují vytvářet přístupné aplikace.

## <a name="accessibility-switches"></a>Přepínače přístupnosti

Aplikaci můžete nakonfigurovat tak, aby se přihlásila k funkcím usnadnění přístupu, pokud cílí na rozhraní .NET Framework 4.7 nebo starší verzi, ale běží v rozhraní .NET Framework 4.7.1 nebo novějším. Aplikaci můžete také nakonfigurovat tak, aby používala starší funkce (a nevyužívala funkce usnadnění), pokud cílí na rozhraní .NET Framework 4.7.1 nebo novější. Každá verze rozhraní .NET Framework, která obsahuje funkce usnadnění přístupu, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) má přepínač [`<runtime>`](../configure-apps/file-schema/runtime/index.md) usnadnění specifický pro verzi, který přidáte do prvku v části konfiguračního souboru aplikace. Podporované přepínače jsou následující:

|Version|Přepínač|
|---|---|
|Rozhraní .NET 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
| .NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|
| .NET Framework 4.8|"Switch.UseLegacyAccessibilityFeatures.3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Využití vylepšení přístupnosti

Nové funkce usnadnění jsou ve výchozím nastavení povoleny pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější. Kromě toho aplikace, které cílí na starší verzi rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.1 nebo novější, se [`<runtime>`](../configure-apps/file-schema/runtime/index.md) mohou odhlásit z chování přístupnosti `false`starší verze (a tím využít vylepšení usnadnění) přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v části konfiguračního souboru aplikace a nastavením jejich hodnoty na . Následující text ukazuje, jak se přihlásit k vylepšením přístupnosti zavedeným v rozhraní .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Pokud se rozhodnete přihlásit k funkcím usnadnění v novější verzi rozhraní .NET Framework, musíte se také explicitně přihlásit k funkcím z dřívějších verzí rozhraní .NET Framework. Konfigurace aplikace tak, aby využívala vylepšení usnadnění v rozhraní .NET Framework 4.7.1 a 4.7.2, vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

Konfigurace aplikace tak, aby využívala vylepšení usnadnění v rozhraní .NET Framework 4.7.1, 4.7.2 a 4.8, vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Obnovení chování starší verze

Aplikace, které cílí na verze rozhraní .NET Framework začínající 4.7.1, mohou [`<runtime>`](../configure-apps/file-schema/runtime/index.md) zakázat funkce usnadnění přidáním přepínačů `true`do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v části konfiguračního souboru aplikace a nastavením jejich hodnoty na . Například následující konfigurace se odhlásí z funkcí usnadnění zavedených v rozhraní .NET Framework 4.7.2:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.8

Rozhraní .NET Framework 4.8 obsahuje nové funkce usnadnění v následujících oblastech:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Návrhář pracovních postupů Nadace pracovního postupu systému Windows (WF)](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a>Windows Forms

V rozhraní .NET Framework 4.8 přidá Windows Forms podporu pro LiveRegions a události oznámení pro mnoho běžně používaných ovládacích prvků. Přidává také podporu pro popisky, když uživatel přejde na ovládací prvek pomocí klávesnice.

**Podpora UIA LiveRegions v popiscích a stavových proužcích**

UIA LiveRegions umožňují vývojářům aplikací upozornit programy pro čtení z obrazovky na změnu textu v ovládacím prvku, který je umístěn na rozdíl od umístění, kde uživatel pracuje. To je užitečné například <xref:System.Windows.Forms.StatusStrip> pro ovládací prvek, který zobrazuje stav připojení. Pokud je připojení přerušeno a stav se změní, může vývojář chtít upozornit program pro čtení z obrazovky.

Počínaje rozhraním .NET Framework 4.8 implementuje windows forms <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> u iia liveregions pro ovládací prvky i ovládací prvky. Například následující kód používá LiveRegion <xref:System.Windows.Forms.Label> v `label1`ovládacím prvku s názvem :

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Předčítání oznamuje "Ready" bez ohledu na to, kde uživatel pracuje s aplikací.

Můžete také implementovat jako <xref:System.Windows.Forms.UserControl> LiveRegion:

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

Událost Oznámení UIA, která byla zavedena v aktualizaci Windows 10 Fall Creators Update, umožňuje vaší aplikaci vyvolat událost UIA, což vede k tomu, že Předčítání jednoduše dělá oznámení na základě textu, který zadáte s událostí, aniž byste museli mít odpovídající ovládací prvek v ui. V některých případech se jedná o jednoduchý způsob, jak výrazně zlepšit dostupnost aplikace. V může být také užitečné upozornit na průběh některého procesu, který může trvat dlouhou dobu. Další informace o událostech oznámení UIA najdete v tématu [Může vaše aplikace klasické pracovní plochy využít novou událost oznámení o uznaci?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).

Následující příklad vyvolá [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Popisy nástrojů pro přístup pomocí klávesnice**

V aplikacích, které cílí na rozhraní .NET Framework 4.7.2 a starší verze, lze aktivovat [pouze popis ovládacího prvku,](xref:System.Windows.Forms.ToolTip) který se zobrazí přesunutím ukazatele myši do ovládacího prvku. Počínaje rozhraním .NET Framework 4.8 může uživatel klávesnice aktivovat popisek ovládacího prvku zaostřením ovládacího prvku pomocí kláves y Tab nebo kláves se šipkami pomocí modifikačních kláves nebo bez něj. Toto konkrétní vylepšení usnadnění vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):

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

Následující obrázek znázorňuje popis, když uživatel vybral tlačítko s klávesnicí.

![Snímek obrazovky s popisem, když uživatel přejde na tlačítko pomocí klávesnice.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Počínaje rozhraním .NET Framework 4.8 obsahuje wpf řadu vylepšení usnadnění.

**Předčítání obrazovky již neoznamují prvky s viditelností Sbalené nebo Skryté**

Prvky se sbalenou nebo skrytou viditelností již program pro čtení z obrazovky neoznamují. Uživatelská rozhraní, která obsahují prvky s viditelnost <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> mohou být zkresleny programy pro čtení z obrazovky, pokud jsou oznámeny uživateli. Počínaje rozhraním .NET Framework 4.8 již WPF neobsahuje sbalené nebo skryté prvky v ovládacím zobrazení stromu UIAutomation, takže programy pro čtení z obrazovky již nemohou tyto prvky oznamovat.

**Vlastnost SelectionTextBrush pro použití s výběrem textu nezaloženým na Adorneru**

V rozhraní .NET Framework 4.7.2 wpf <xref:System.Windows.Controls.TextBox> přidal <xref:System.Windows.Controls.PasswordBox> možnost kreslit a výběr textu bez použití vrstvy Adorner. Barva popředí vybraného textu v tomto scénáři <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>byla dána .

Rozhraní .NET Framework 4.8 `SelectionTextBrush`přidá novou vlastnost , která umožňuje vývojářům vybrat konkrétní stopu pro vybraný text při použití výběru textu nezaložené na Adorner. Tato vlastnost funguje <xref:System.Windows.Controls.Primitives.TextBoxBase>pouze na -derived ovládací prvky a <xref:System.Windows.Controls.PasswordBox> ovládací prvek v aplikacích WPF s non-Adorner-založené výběr textu povolena. Nefunguje na ovládací <xref:System.Windows.Controls.RichTextBox> prvek. Pokud není povolen výběr textu na bázi Adorner, tato vlastnost je ignorována.

Chcete-li použít tuto vlastnost, jednoduše ji přidejte do kódu XAML a použijte příslušnou stopu nebo vazbu. Výsledný výběr textu vypadá takto:

![Snímek obrazovky aplikace spuštěné se slovy Hello World selected.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

Můžete kombinovat použití `SelectionBrush` vlastností `SelectionTextBrush` a generovat libovolnou kombinaci barev pozadí a popředí, kterou považujete za vhodnou.

**Podpora vlastnosti UIAutomation ControllerFor**

`ControllerFor` UIAutomation vlastnost vrátí pole automatizace prvků, které jsou manipulovány prvkautomatizace, který podporuje tuto vlastnost. Tato vlastnost se běžně používá pro automatické navrhování usnadnění přístupu. `ControllerFor`se používá, když prvek automatizace ovlivňuje jeden nebo více segmentů uživatelského rozhraní aplikace nebo plochy. V opačném případě je obtížné přidružit dopad operace ovládacího prvku s prvky uživatelského rozhraní. Tato funkce přidává možnost pro ovládací prvky poskytnout hodnotu `ControllerFor` pro vlastnost.

Rozhraní .NET Framework 4.8 přidává <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>novou virtuální metodu . . Chcete-li zadat `ControllerFor` hodnotu vlastnosti, jednoduše přepsat `List<AutomationPeer>` tuto metodu a <xref:System.Windows.Automation.Peers.AutomationPeer>vrátit pro ovládací prvky, s nimiž se manipuluje tímto :

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

**Popisy k přístupu z klávesnice**

V rozhraní .NET Framework 4.7.2 a starších verzích se popisky zobrazují pouze v případě, že uživatel najedete kurzorem myši nad ovládacím prvkem. V rozhraní .NET Framework 4.8 se popisky zobrazují také na fokusklávesnice a také pomocí klávesové zkratky.

Chcete-li tuto funkci povolit, aplikace musí cílit na rozhraní `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework 4.8 nebo opt-in pomocí přepínačů a `Switch.UseLegacyToolTipDisplay` [AppContext.](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) Následuje ukázkový konfigurační soubor aplikace:

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

Po povolení se všechny ovládací prvky, které obsahují popisek, zobrazí, jakmile ovládací prvek obdrží fokus klávesnice. Popisek lze v průběhu času nebo při změně fokusu klávesnice zavřít. Uživatelé mohou také ručně zavřít popisek pomocí nové klávesové zkratky Ctrl + Shift + F10. Jakmile je popisek zamítnut, lze jej znovu zobrazit pomocí stejné klávesové zkratky.

> [!NOTE]
> [Popisky pásu karet](xref:System.Windows.Controls.Ribbon.RibbonToolTip) na <xref:System.Windows.Controls.Ribbon.Ribbon> ovládacích prvcích se při fokusu klávesnice nezobrazují; zobrazují se pouze pomocí klávesové zkratky.

**Přidána podpora vlastností SizeOfSet a PositionInSet UIAutomation**

Windows 10 představil dvě nové vlastnosti UIAutomation `SizeOfSet` a `PositionInSet`, které používají aplikace k popisu počtu položek v sadě. UIAutomation klientské aplikace, jako jsou programy pro čtení z obrazovky pak dotaz aplikace pro tyto vlastnosti a oznámit přesnou reprezentaci uživatelského rozhraní aplikace.

Počínaje rozhraním .NET Framework 4.8 wpf zpřístupňuje tyto dvě vlastnosti UIAutomation v aplikacích WPF. Toho lze dosáhnout dvěma způsoby:

- Pomocí vlastností závislostí.

  WPF přidá dvě nové <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> vlastnosti závislostí a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>. Vývojář může použít XAML k nastavení jejich hodnot:

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- Přepsáním AutomationPeer virtuální metody.

  A <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtuální metody byly přidány do třídy AutomationPeer. Vývojář může poskytnout `SizeOfSet` hodnoty `PositionInSet` pro a přepsáním těchto metod, jak je znázorněno v následujícím příkladu:

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

Kromě toho položky v <xref:System.Windows.Controls.ItemsControl> instancích poskytují hodnotu pro tyto vlastnosti automaticky bez další akce od vývojáře. Pokud <xref:System.Windows.Controls.ItemsControl> je seskupena, kolekce skupin je reprezentována jako sada a každá skupina se počítá jako samostatná sada, přičemž každá položka uvnitř této skupiny poskytuje své umístění uvnitř této skupiny a velikost skupiny. Automatické hodnoty nejsou ovlivněny virtualizací. I v případě, že položka není realizována, je stále započítána do celkové velikosti sady a ovlivňuje pozici v sadě položek na stejné úrovni.

Automatické hodnoty jsou k dispozici pouze v případě, že aplikace cíle .NET Framework 4.8. U aplikací, které cílí na starší verzi rozhraní `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework, můžete nastavit [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App.config:

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

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Návrhář pracovních postupů Nadace pracovního postupu systému Windows (WF)

Návrhář pracovního postupu obsahuje následující změny v rozhraní .NET Framework 4.8:

- Uživatelům používajícím Předčítání se zobrazí vylepšení popisků případu FlowSwitch.

- Uživatelům používajícím Předčítání se zobrazí vylepšení v popisech tlačítek.

- Uživatelům, kteří zvolí motivy s vysokým kontrastem, se zobrazí vylepšení viditelnosti návrháře pracovních postupů a jeho ovládacích prvků, jako jsou lepší kontrastní poměry mezi prvky a výraznější výběrová pole používaná pro prvky fokusu.

Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7.2 nebo `Switch.UseLegacyAccessibilityFeatures.3` starší verzi, `false` můžete se k těmto změnám přihlásit nastavením [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v konfiguračním souboru aplikace. Další informace naleznete v části [Využití vylepšení usnadnění](#taking-advantage-of-accessibility-enhancements) v tomto článku.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.7.2

Rozhraní .NET Framework 4.7.2 obsahuje nové funkce usnadnění v následujících oblastech:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Barvy definované oS v motivech s vysokým kontrastem**

Počínaje rozhraním .NET Framework 4.7.2 používá systém Windows Forms barvy definované operačním systémem v motivech s vysokým kontrastem. To má vliv na následující ovládací prvky:

- Šipka rozevíracího <xref:System.Windows.Forms.ToolStripDropDownButton> seznamu ovládacího prvku.

- Ovládací <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> prvky <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> a <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ovládací <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>prvky s nastavenou na nebo . Dříve nebyly vybrané barvy textu a pozadí kontrastní a byly těžko čitelné.

- Ovládací prvky <xref:System.Windows.Forms.GroupBox> obsažené v <xref:System.Windows.Forms.Control.Enabled> rámci, `false`který má svou vlastnost nastavenou na .

- Ovládací <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox>prvky <xref:System.Windows.Forms.ToolStripDropDownButton> , a ovládací prvky, které mají zvýšený kontrastní poměr světelnosti v režimu vysokého kontrastu.

- Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Vylepšení předčítání**

Počínaje rozhraním .NET Framework 4.7.2 je podpora předčítání vylepšena takto:

- Oznamuje hodnotu vlastnosti <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při oznámení textu <xref:System.Windows.Forms.ToolStripMenuItem>.

- Označuje, <xref:System.Windows.Forms.ToolStripMenuItem> kdy má <xref:System.Windows.Forms.Control.Enabled> vlastnost `false`nastavena na .

- Poskytuje zpětnou vazbu o stavu <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> zaškrtávacího políčka, když je vlastnost nastavena na `true`.

- Pořadí fokusu režimu skenování předčítání je konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně stahování ClickOnce.

**Vylepšení datagridview**

Počínaje rozhraním .NET Framework 4.7.2 ovládací <xref:System.Windows.Forms.DataGridView> prvek zavedl následující vylepšení usnadnění:

- Řádky lze seřadit pomocí klávesnice. Uživatel může použít klávesu F3 k řazení podle aktuálního sloupce.

- Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je hodnota <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>nastavena na , záhlaví sloupce změní barvu, aby označilo aktuální sloupec jako karty uživatele prostřednictvím buněk v aktuálním řádku.

- Vlastnost <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správný nadřazený ovládací prvek.

**Vylepšené vizuální podněty**

- Ovládací <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> prvky a <xref:System.Windows.Forms.ButtonBase.Text> s prázdnou vlastností zobrazí indikátor fokusu, když obdrží fokus.

**Vylepšená podpora mřížky vlastností**

- Podřízené <xref:System.Windows.Forms.PropertyGrid> prvky ovládacího prvku nyní vrátí a `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pouze v případě, že propertyGrid element je povolena.

- Podřízené <xref:System.Windows.Forms.PropertyGrid> prvky `false` ovládacího <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> prvku vrátí a pro vlastnost pouze v případě, že propertygrid element může změnit uživatel.

**Vylepšená navigace pomocí klávesnice**

- Ovládací <xref:System.Windows.Forms.ToolStripButton> prvek umožňuje zaostření, pokud je obsažen v <xref:System.Windows.Forms.ToolStripPanel> rámci, který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavenou na`true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Změny ovládacích prvků CheckBox a RadioButton**

V rozhraní .NET Framework 4.7.1 a <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> starších verzích wpf a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládací prvky mají nekonzistentní a v klasické a vysoké kontrastní motivy nesprávné fokus vizuály.  K těmto problémům dochází v případech, kdy ovládací prvky nemají žádný obsah nastaven.  To může způsobit, že přechod mezi motivy bude matoucí a vizuální fokus bude těžko vidět.

V rozhraní .NET Framework 4.7.2 jsou tyto vizuály nyní konzistentnější napříč motivy a snadněji viditelné v motivech Classic a High Contrast.

**Ovládací prvky WinForms hostované v aplikaci WPF**

Pro ovládací prvek WinForms hostovaný v aplikaci WPF v rozhraní .NET Framework 4.7.1 a starších verzích nemohli uživatelé z <xref:System.Windows.Forms.Integration.ElementHost> vrstvy WinForms out out z vrstvy WinForms, pokud je prvním nebo posledním ovládacím prvkem v této vrstvě ovládací prvek WPF. V rozhraní .NET Framework 4.7.2 mohou uživatelé nyní out out vrstvy WinForms.

Automatizované aplikace, které spoléhají na fokus, však nemusí fungovat podle očekávání.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>Co je nového v usnadnění v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 obsahuje nové funkce usnadnění v následujících oblastech:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET webové ovládací prvky](#aspnet471)

- [Nástroje sady .NET SDK](#tools471)

- [Návrhář pracovních postupů nadace Windows Workflow Foundation (WF)](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Vylepšení čtečky obrazovky**

Pokud jsou povolena vylepšení usnadnění přístupu, obsahuje rozhraní .NET Framework 4.7.1 následující vylepšení, která ovlivňují programy pro čtení z obrazovky:

- V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.Expander> a starších verzích byly ovládací prvky oznámeny programy pro čtení z obrazovky jako tlačítka. Počínaje rozhraním .NET Framework 4.7.1 jsou správně oznámeny jako rozbalitelné/sbalitelné skupiny.

- V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.DataGridCell> a starších verzích byly ovládací prvky programy pro čtení z obrazovky označeny jako "vlastní". Počínaje rozhraním .NET Framework 4.7.1 jsou nyní správně oznámeny jako buňka datové mřížky (lokalizované).

- Počínaje rozhraním .NET Framework 4.7.1 programy pro <xref:System.Windows.Controls.ComboBox>čtení z obrazovky oznamují název upravitelného .

- V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.PasswordBox> a starších verzích byly ovládací prvky oznámeny jako "žádná položka v zobrazení" nebo měly jinak nesprávné chování. Tento problém je vyřešen počínaje rozhraním .NET Framework 4.7.1.

**Podpora pro UIAutomation LiveRegion**

Programy pro čtení z obrazovky, jako je Předčítání, pomáhají lidem číst obsah ui aplikace, obvykle pomocí výstupu převodu textu na řeč obsahu ui, který má fokus. Pokud se však prvek uživatelského rozhraní změní a nemá fokus, uživatel nemusí být upozorněn a může chybět důležité informace. Živé regiony se zaměřují na řešení tohoto problému. Vývojář je může použít k informování čtečky obrazovky nebo jiného klienta UIAutomation, že byla provedena důležitá změna prvku uživatelského rozhraní. Program pro čtení z obrazovky se pak může rozhodnout, jak a kdy o této změně informuje uživatele.

Pro podporu živých oblastí byla do WPF přidána následující api:

- Pole <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> a, která identifikují vlastnost **LiveSetting** a událost **LiveRegionChanged.** Lze je nastavit pomocí XAML.

- **AutomationProperties.LiveSetting** připojené vlastnosti, která informuje čtečku obrazovky o významu změny uživatelského rozhraní pro uživatele.

- Vlastnost, <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> která identifikuje **AutomationProperties.LiveSetting** připojené vlastnosti.

- Metoda, <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> která může být přepsána poskytnout **LiveSetting** hodnotu.

- Metody <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> a, které získat a nastavit **LiveSetting** hodnotu.

- Výčet, <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> který definuje následující možné **LiveSetting** hodnoty:

  - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Prvek neodesílá oznámení, pokud došlo ke změně obsahu živé oblasti.
  - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Prvek odesílá nepřerušitelná oznámení, pokud došlo ke změně obsahu živé oblasti.

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Prvek odešle přerušená oznámení, pokud došlo ke změně obsahu živé oblasti.

LiveRegion můžete vytvořit nastavením **AutomationProperties.LiveSetting** vlastnost na prvek zájmu, jak je znázorněno v následujícím příkladu:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Když se změní data v živé oblasti a potřebujete informovat program pro čtení z obrazovky, explicitně vyvoláte událost, jak je znázorněno v následující ukázce.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Vysoký kontrast**

Počínaje rozhraním .NET Framework 4.7.1 bylo u různých ovládacích prvků WPF provedeno zlepšení vysokého kontrastu. Nyní jsou viditelné <xref:System.Windows.SystemParameters.HighContrast%2A> při nastavení motivu. Mezi ně patří:

- <xref:System.Windows.Controls.Expander>Ovládací prvek

  Vizuální fokus <xref:System.Windows.Controls.Expander> pro ovládací prvek je nyní viditelný. Vizuály <xref:System.Windows.Controls.ComboBox>klávesnice<xref:System.Windows.Controls.ListBox>pro <xref:System.Windows.Controls.RadioButton> , a ovládací prvky jsou také viditelné. Například:

  Před:

  ![Snímek obrazovky ovládacího prvku expanderu s fokusem a bez fokusu vizuálu](./media/whats-new-in-accessibility/expander-control-before.png)

  Po:

  ![Snímek obrazovky ovládacího prvku expander s fokusem zobrazující tečkovanou čáru kolem textu ovládacího prvku](./media/whats-new-in-accessibility/expander-control-after.png)

- <xref:System.Windows.Controls.CheckBox>a <xref:System.Windows.Controls.RadioButton> ovládací prvky

  Text v <xref:System.Windows.Controls.CheckBox> ovládacích prvcích a <xref:System.Windows.Controls.RadioButton> je nyní lépe vidět, když je vybrán v motivech s vysokým kontrastem. Například:

  Před:

  ![Snímek obrazovky s přepínači a kontrolními tlačítky se špatnou viditelností textu na motivech s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  Po:

  ![Snímek obrazovky s přepínači a kontrolními tlačítky s lepší viditelností textu na motivy s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>Ovládací prvek

  Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Windows.Controls.ComboBox> má ohraničení zakázaného ovládacího prvku stejnou barvu jako zakázaný text. Například:

  Před:

  ![Snímek obrazovky se zakázaným rámečkem Se seznamem s textem ohraničení a ovládacích prvku v různých barvách](./media/whats-new-in-accessibility/combo-disabled-before.png)

  Po:

  ![Snímek obrazovky se zakázaným rámečkem ComboBox s ohraničením stejné barvy jako text ovládacího prvku](./media/whats-new-in-accessibility/combo-disabled-after.png)

  Kromě toho, zdravotně a soustředěné tlačítka používají správnou barvu motivu.

  Před:

  ![Snímek obrazovky s černým tlačítkem s šedým textem Focus Me](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  Po:

  ![Snímek obrazovky s modrým tlačítkem s černým textem Focus Me](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  Nakonec v rozhraní .NET Framework 4.7 a <xref:System.Windows.Controls.ComboBox> starších verzích nastavení stylu ovládacího prvku způsobilo, že `Toolbar.ComboBoxStyleKey` šipka rozevíracího seznamu byla neviditelná. Tento problém je vyřešen počínaje rozhraním .NET Framework 4.7.1. Například:

  Před:

  ![Snímek obrazovky ovládacího prvku ComboBox s neviditelnou šipkou rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  Po:

  ![Snímek obrazovky ovládacího prvku ComBoxBox zobrazujícího šipku rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <xref:System.Windows.Controls.DataGrid>Ovládací prvek

  Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Windows.Controls.DataGrid> nyní šipka indikátoru řazení v ovládacích prvcích používá správné barvy motivu. Například:

  Před:

  ![Snímek obrazovky se šipkou indikátoru řazení před vylepšeními](./media/whats-new-in-accessibility/sort-indicator-before.png)

  Po:

  ![Snímek obrazovky se šipkou indikátoru řazení po vylepšeních](./media/whats-new-in-accessibility/sort-indicator-after.png)

  Kromě toho v rozhraní .NET Framework 4.7 a starších verzích se výchozí styl propojení změnil na nesprávnou barvu na myši v režimech vysokého kontrastu. To je vyřešen počínaje rozhraním .NET Framework 4.7.1. Podobně <xref:System.Windows.Controls.DataGrid> zaškrtávací políčko sloupce používá očekávané barvy pro zpětnou vazbu fokus klávesnice počínaje rozhraním .NET Framework 4.7.1.

  Před:

  ![Snímek obrazovky s odkazem na tlačítko Klikněte na mě! červeně.](./media/whats-new-in-accessibility/default-link-style-before.png)

  Po:

  ![Snímek obrazovky s odkazem na tlačítko Klikněte na mě! žlutě.](./media/whats-new-in-accessibility/default-link-style-after.png)

Další informace o vylepšení wpf usnadnění v rozhraní .NET Framework 4.7.1 naleznete [v tématu usnadnění zlepšení WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Vylepšení usnadnění přístupu pro Windows Forms

V rozhraní .NET Framework 4.7.1 obsahuje formuláře systému Windows (WinForms) změny usnadnění přístupu v následujících oblastech.

**Vylepšené zobrazení v režimu vysokého kontrastu**

Počínaje rozhraním .NET Framework 4.7.1 nabízejí různé ovládací prvky WinForms vylepšené vykreslování v režimech HighContrast dostupných v operačním systému. Systém Windows 10 změnil hodnoty pro některé barvy systému s vysokým kontrastem a windows forms je založen na rozhraní Windows 10 Win32. Chcete-li získat nejlepší zážitek, spusťte nejnovější verzi systému Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru app.manifest do testovací aplikace a odkomentujte řádek podporovaného operačního systému Windows 10 tak, aby vypadal takto:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

Některé příklady změn s vysokým kontrastem:

- Zaškrtnutí <xref:System.Windows.Forms.MenuStrip> položek se snadněji zobrazují.

- Pokud je <xref:System.Windows.Forms.MenuStrip> tato možnost vybrána, zakázané položky se snadněji zobrazují.

- Text ve <xref:System.Windows.Forms.Button> vybraném ovládacím prvku kontrastuje s barvou výběru.

- Zakázaný text je čitelnější. Například:

  Před:

  ![Snímek obrazovky s aplikací, která používá různé ovládací prvky spuštěné v režimu vysokého kontrastu před vylepšením usnadnění přístupu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  Po:

  ![Snímek obrazovky s aplikací, která používá různé ovládací prvky spuštěné v režimu vysokého kontrastu po vylepšení usnadnění přístupu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- Vylepšení vysokého kontrastu v dialogovém okně výjimky vlákna.

**Vylepšená podpora pro Předčítání**

Windows Forms v rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení usnadnění pro Předčítání:

- Ovládací <xref:System.Windows.Forms.MonthCalendar> prvek je přístupný předčítáním, stejně jako další nástroje pro automatizaci uživatelského rozhraní.

- Ovládací <xref:System.Windows.Forms.CheckedListBox> prvek upozorní Předčítání, když se změní stav kontroly položky, aby byl uživatel upozorněn, že změnil hodnotu položky seznamu.

- Ovládací <xref:System.Windows.Forms.DataGridViewCell> prvek hlásí Předčítání správný stav jen pro čtení.

- Předčítání teď může <xref:System.Windows.Forms.ToolStripMenuItem> číst zakázaný text, zatímco dříve přeskakovat zakázané položky nabídky.

**Vylepšená podpora vzorců usnadnění uIAutomation**

Počínaje rozhraním .NET Framework 4.7.1 mohou vývojáři nástrojů pro usnadnění přístupu využít běžné vzory a vlastnosti rozhraní API pro několik ovládacích prvků WinForms. Mezi tato vylepšení usnadnění patří:

- A <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> nyní podporují [rozbalení/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- Nyní <xref:System.Windows.Forms.DataGridViewCheckBoxCell> podporuje [přepínací vzor](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).

- Ovládací <xref:System.Windows.Forms.ToolStripItem> prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> podporuje vlastnost a [rozbalení/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- A <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> ovládací prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> podporují vlastnost.

**Vylepšené prostředí prohlížeče vlastností**

Počínaje rozhraním .NET Framework 4.7.1 obsahuje windows forms:

- Lepší navigace pomocí klávesnice v různých rozbalovacích oknech výběru.
- Snížení zbytečných zarážek tabulátoru.
- Lepší vykazování typů ovládacích prvku.
- Vylepšené chování předčítání.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>ASP.NET webové ovládací prvky

Počínaje rozhraními .NET Framework 4.7.1 a Visual Studio 2017 verze 15.3 ASP.NET vylepšuje způsob, jakým ASP.NET webové ovládací prvky fungují s technologií usnadnění v sadě Visual Studio. Změny zahrnují následující:

- Změny pro implementaci chybějících vzorů usnadnění přístupu k rozhraní v ovládacích prvcích, jako je dialogové okno **Přidat pole** v **průvodci zobrazením podrobností** nebo dialogové okno **Konfigurovat zobrazení seznamu** průvodce **listview.**

- Změny pro zlepšení zobrazení v režimu vysokého kontrastu, například **Editor polí datových stránek**.

- Změny pro zlepšení prostředí navigace pomocí klávesnice pro ovládací prvky, například dialogové okno **Pole** v průvodci **Upravit pole operátoru** ovládacího prvku DataPager, dialogové okno **Konfigurovat kontext objektu** nebo dialogové okno **Konfigurovat výběr dat** průvodce Konfigurovat **zdroj dat.**

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>Nástroje sady .NET SDK

Nástroj [Editor konfigurace (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých problémů s přístupností. Většina z nich byly malé problémy, jako je název, který není definován nebo některé vzory automatizace uživatelského rozhraní nejsou implementovány správně. Zatímco mnoho uživatelů nebude vědět o těchto nesprávných hodnotách, zákazníci, kteří používají asistenční technologie, jako jsou programy pro čtení z obrazovky, najdou tyto nástroje sady SDK přístupnější.

Tato vylepšení změnit některé předchozí chování, jako je například pořadí fokusu klávesnice.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Návrhář pracovních postupů nadace Windows Workflow Foundation (WF)

Změny usnadnění v Návrháři pracovních postupů zahrnují následující:

- Pořadí polí se v některých ovládacích prvcích mění zleva doprava a shora dolů:

  - Okno inicializovat korelace pro <xref:System.ServiceModel.Activities.InitializeCorrelation> nastavení dat korelace pro aktivitu.

  - Okno definice obsahu <xref:System.ServiceModel.Activities.Receive>pro <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply> , a aktivity.

- Další funkce jsou k dispozici prostřednictvím klávesnice:

  - Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny pomocí klávesnice při prvním zaměření.

  - Výstražné ikony jsou přístupné pomocí klávesnice.

  - Tlačítko **Další vlastnosti** v okně **Vlastnosti** je přístupné pomocí klávesnice.

  - Uživatelé klávesnice mají přístup k položkám záhlaví v podokně **Argumenty** a **proměnné** návrháře pracovních postupů.

- Lepší viditelnost položek s fokusem, například když:

  - Přidání řádků do datových mříží používaných návrhářem pracovních postupů a návrháři aktivit.

  - Procházení polí v <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> a aktivity.

  - Nastavení výchozích hodnot pro proměnné nebo argumenty

- Programy pro čtení z obrazovky nyní správně rozpoznávají:

  - Zarážky nastavené v návrháři pracovního postupu.

  - V <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>oblasti <xref:System.ServiceModel.Activities.CorrelationScope> , a aktivity.
  - Obsah aktivity. <xref:System.ServiceModel.Activities.Receive>

  - Cílový typ aktivity. <xref:System.Activities.Statements.InvokeMethod>

  - Pole se seznamem Výjimka a <xref:System.Activities.Statements.TryCatch> finally části v aktivitě.

  - Pole se seznamem Typ zprávy, rozdělovač v okně Přidat inicializační stavkovy korelace, okno Definice<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>obsahu <xref:System.ServiceModel.Activities.SendReply>a <xref:System.ServiceModel.Activities.ReceiveReply>okno Definice korelování v aktivitách zasílání zpráv ( , , , a ).

  - Přechody a přechody stavových přechodů.

  - Poznámky a konektory <xref:System.Activities.Statements.FlowDecision> na aktivity.

  - Kontextové nabídky (kliknutí pravým tlačítkem myši) pro aktivity.

  - Editory hodnot vlastností, tlačítko Vymazat hledání, tlačítka Podle kategorie a Abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.

  - Procento zvětšení v Návrháři pracovního postupu.

  - Oddělovač <xref:System.Activities.Statements.Parallel> v <xref:System.Activities.Statements.Pick> a aktivity.

  - Aktivita. <xref:System.Activities.Statements.InvokeDelegate>

  - Okno Vybrat typy pro aktivity slovníku (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, atd.).

  - Okno Procházet a vybrat typ rozhraní .NET.

  - Popis cesty v Návrháři pracovního postupu.

- Uživatelům, kteří zvolí motivy s vysokým kontrastem, se zobrazí mnoho vylepšení viditelnosti návrháře pracovních postupů a jeho ovládacích prvků, jako jsou lepší kontrastní poměry mezi prvky a výraznější výběrová pole používaná pro prvky fokusu.

## <a name="see-also"></a>Viz také

- [Novinky v rozhraní .NET Framework](index.md)
