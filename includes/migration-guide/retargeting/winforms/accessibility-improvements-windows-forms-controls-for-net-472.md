---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614567"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>Vylepšení usnadnění v model Windows Forms ovládacích prvcích pro .NET 4.7.2

#### <a name="details"></a>Podrobnosti

Model Windows Forms Framework vylepšuje, jak funguje s technologiemi usnadnění, aby lépe podporovaly model Windows Forms zákazníky. Mezi ně patří tyto změny:

- Změny pro zlepšení zobrazení v režimu Vysoký kontrast.
- Změny pro zlepšení navigace klávesnice v ovládacích prvcích DataGridView a MenuStrip.
- Změny interakce s programem Narrator.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Zkompiluje se znovu a zacílí na .NET Framework 4.7.2. Tyto změny přístupnosti jsou ve výchozím nastavení povolené v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.
- Cílí na .NET Framework 4.7.1 nebo starší verze a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

Mějte na paměti, že pokud se chcete přihlásit k funkcím pro usnadnění přidaným v .NET Framework 4.7.2, musíte také vyjádřit výslovný souhlas s funkcemi přístupnosti .NET Framework 4.7.1. Aplikace, které cílí na .NET Framework 4.7.2 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .

**Použití barev definovaných operačním systémem v motivech Vysoký kontrast**

- Šipka rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton> nyní používá barvy definované operačním systémem v vysoký kontrastm motivu.
- <xref:System.Windows.Forms.Button><xref:System.Windows.Forms.RadioButton>a <xref:System.Windows.Forms.CheckBox> ovládací prvky s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavenou <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> nyní používají barvy definované operačním systémem v vysoký kontrast motiv, pokud je vybrán. Dříve byly barvy textu a pozadí Nekontrastní a bylo těžké je přečíst.
- Ovládací prvky obsažené v rámci <xref:System.Windows.Forms.GroupBox> , které mají svou <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na, `false` budou nyní používat barvy definované operačním systémem v vysoký kontrastm motivu.
- <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> Ovládací prvky, a <xref:System.Windows.Forms.ToolStripDropDownButton> mají v režimu Vysoký kontrast vyšší poměr jasu a kontrast.
- <xref:System.Windows.Forms.DataGridViewLinkCell>ve výchozím nastavení použije barvy definované operačním systémem v režimu Vysoký kontrast pro danou <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType> vlastnost.
Poznámka: Windows 10 změnil hodnoty pro některé systémové barvy s vysokým kontrastem. Rozhraní model Windows Forms Framework vychází z rozhraní Win32. Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru App. manifest do testovací aplikace a zrušením komentáře k následujícímu kódu:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Vylepšená podpora Narrator**

- Program Narrator nyní oznamuje hodnotu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> vlastnosti při oznamování textu <xref:System.Windows.Forms.ToolStripMenuItem> .
- Narrator teď indikuje, kdy <xref:System.Windows.Forms.ToolStripMenuItem> má <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na `false` .
- Program Narrator nyní poskytuje zpětnou vazbu ke stavu zaškrtávacího políčka, pokud <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je vlastnost nastavena na hodnotu `true` .
- Pořadí fokusu v režimu kontroly mluveného komentáře je teď konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně pro stažení ClickOnce.

**Vylepšená podpora usnadnění přístupu DataGridView**

- Řádky v a se <xref:System.Windows.Forms.DataGridView> teď dají seřadit pomocí klávesnice. Nyní může uživatel použít klávesu F3, aby bylo možné řadit podle aktuálního sloupce.
- Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , změní se barva záhlaví sloupce tak, aby označovalo aktuální sloupec jako karty uživatelů na aktuálním řádku.
- <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType>Vlastnost teď vrací správný nadřazený ovládací prvek.

**Vylepšené vizuální pomůcky**

- <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastností budou nyní po obdržení fokusu zobrazovat indikátor fokusu.

**Vylepšená podpora mřížky vlastností**

- <xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku nyní vrátí `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pro vlastnost pouze v případě, že je povolen prvek PropertyGrid.
- <xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku nyní vrátí `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost pro vlastnost pouze v případě, že uživatel může změnit element PropertyGrid.
Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</p>**Vylepšená navigace klávesnicí**

- <xref:System.Windows.Forms.ToolStripButton>teď umožňuje fokus, pokud je obsažený v <xref:System.Windows.Forms.ToolStripPanel> , který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavenou na `true` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
