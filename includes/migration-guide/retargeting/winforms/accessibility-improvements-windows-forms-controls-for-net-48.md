---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616241"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>Vylepšení usnadnění v ovládacích prvcích model Windows Forms pro .NET 4,8

#### <a name="details"></a>Podrobnosti

Rozhraní model Windows Forms Framework pokračuje v vylepšování toho, jak funguje s technologiemi usnadnění pro lepší podporu model Windows Formsch zákazníků. Mezi ně patří tyto změny:

- Změny pro zlepšení zobrazení v režimu Vysoký kontrast.
- Změny interakce s programem Narrator.
- Změny v přístupné hierarchii (Vylepšení navigace prostřednictvím stromu automatizace uživatelského rozhraní).

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4,8. Aplikace se může přihlásit k těmto změnám jedním z následujících způsobů:

- Zkompiluje se znovu a zacílí na .NET Framework 4,8. Tyto změny přístupnosti jsou ve výchozím nastavení povolené v aplikacích model Windows Forms, které cílí na .NET Framework 4,8.
- Cílí na .NET Framework 4.7.2 nebo starší verze a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

Všimněte si, že pokud se chcete přihlásit k funkcím pro usnadnění přidaným v .NET Framework 4,8, musíte také vyjádřit souhlas s funkcemi přístupnosti .NET Framework 4.7.1 a 4.7.2. Aplikace, které cílí na .NET Framework 4,8 a chtějí zachovat starší možnosti přístupnosti, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu, a to explicitně nastavením tohoto přepínače AppContext na `true` . Povolení podpory vyvolání popisku klávesnice vyžaduje přidání `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` řádku k hodnotě AppContextSwitchOverrides:

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

Upozorňujeme, že povolení této funkce vyžaduje, abyste se při4.7.1I k výše uvedeným funkcím pro usnadnění přístupu .NET Framework 4,8. V případě, že se některé funkce přístupnosti nepovolují, ale v nástroji se zobrazí funkce zobrazení popisu, <xref:System.NotSupportedException> vyvolá se při prvním přístupu k těmto funkcím modul runtime. Zpráva o výjimce indikuje, že popisky klávesnice vyžadují, aby byla povolená vylepšení přístupnosti úrovně 3.

**Použití barev definovaných operačním systémem v motivech Vysoký kontrast**

- Vylepšené motivy s vysokým kontrastem.

**Vylepšená podpora Narrator**

- Program Narrator nyní oznamuje směr řazení <xref:System.Windows.Forms.DataGridViewColumn> Při oznamování přístupového názvu a <xref:System.Windows.Forms.DataGridViewCell> .

**Vylepšená podpora usnadnění CheckedListBox**

- Vylepšená podpora Narrator pro <xref:System.Windows.Forms.CheckedListBox> ovládací prvek. Při přechodu k <xref:System.Windows.Forms.CheckedListBox> ovládacímu prvku pomocí klávesnice se program Narrator zaměřuje na <xref:System.Windows.Forms.CheckedListBox> položku a oznamuje ji.
- Prázdný ovládací prvek CheckedListBox nyní obsahuje obdélník fokusu pro virtuální první položku, pokud se ovládací prvek změní na fokus.

**Vylepšená podpora funkce ComboBox**

- Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ComboBox> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.
**Vylepšená podpora usnadnění přístupu DataGridView**

- Povolená Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.DataGridView> řízení s možností používat oznámení automatizace uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.
- Prvek automatizace uživatelského rozhraní, který odpovídá <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> nebo <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> je nyní podřízenosti odpovídající buňky pro úpravy.

**Vylepšená podpora usnadnění LinkLabel**

- Vylepšené <xref:System.Windows.Forms.LinkLabel> přístupnost ovládacího prvku: Narrator oznamuje zakázaný stav odkazu, pokud je odpovídající <xref:System.Windows.Forms.LinkLabel> ovládací prvek zakázán.

**Vylepšená podpora funkcí ProgressBar**

- Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ProgressBar> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní. Vývojáři teď můžou používat upozornění na automatizaci uživatelského rozhraní, které může program Narrator oznámit, aby označoval průběh.
Přehled událostí automatizace uživatelského rozhraní, včetně událostí oznámení automatizace uživatelského rozhraní, najdete v tématu [Přehled událostí automatizace](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)uživatelského rozhraní.

**Vylepšená podpora funkcí PropertyGrid**

- Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.PropertyGrid> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.
- Prvek automatizace uživatelského rozhraní, který odpovídá aktuálně upravované vlastnosti, je nyní podřízenou položkou příslušného elementu automatizace uživatelského rozhraní pro položku vlastností.
- Prvek položky vlastnosti automatizace uživatelského rozhraní je nyní podřízenou položkou odpovídajícího prvku kategorie, pokud <xref:System.Windows.Forms.PropertyGrid> je nadřazený ovládací prvek nastaven na zobrazení kategorií.

**Vylepšená podpora ovládacího prvku ToolStrip**

- Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ToolStrip> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.
- Vylepšená navigace prostřednictvím <xref:System.Windows.Forms.ToolStrip> položek
- V režimu položek nezmizí fokus Předčítání a nepřejde na skryté položky.

**Vylepšené vizuální pomůcky**

- Prázdný <xref:System.Windows.Forms.CheckedListBox> ovládací prvek nyní zobrazuje indikátor fokusu, když dostane fokus.
Poznámka: Podpora automatizace uživatelského rozhraní je povolená pro ovládací prvky v modulu runtime, ale nepoužívá se v době návrhu. Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

**Vyvolání popisů ovládacích prvků pomocí klávesnice**

- Popis ovládacího prvku se teď dá vyvolat tak, že se ovládací prvek vymění pomocí klávesnice. Tato funkce musí být pro aplikaci explicitně povolená (viz část ** &quot; jak tyto změny &quot; výslovně zapnout nebo**vypnout).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4,8         |
| Typ    | Změna cílení |
