---
ms.openlocfilehash: 47d3829748deef2c7c3610816b8941bf88da7ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614589"
---
### <a name="accessibility-improvements-in-wpf"></a>Vylepšení usnadnění v WPF

#### <a name="details"></a>Podrobnosti

**Vylepšení Vysoký kontrast**
<ul><li>Fokus <xref:System.Windows.Controls.Expander> ovládacího prvku je nyní viditelný. V předchozích verzích .NET Framework nebyl.
-Text v <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> ovládacím prvku a ovládací prvky, pokud jsou vybrány, je nyní snazší zobrazit než v předchozích .NET Framework verzích.
-Ohraničení zakázané <xref:System.Windows.Controls.ComboBox> je teď stejnou barvou jako zakázaný text. V předchozích verzích .NET Framework nebyl.
-Zakázaná a zaměřená tlačítka teď používají správnou barvu motivu. V předchozích verzích .NET Framework neexistovaly.
-Rozevírací tlačítko je nyní viditelné <xref:System.Windows.Controls.ComboBox> , pokud je styl ovládacího prvku nastaven na hodnotu <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> v předchozích verzích .NET Framework, nikoli.
-Šipka indikátoru řazení v <xref:System.Windows.Controls.DataGrid> ovládacím prvku teď používá barvy motivu. V předchozích verzích .NET Framework neexistovaly.
-Výchozí styl hypertextového odkazu se nyní změní na správnou barvu motivu při stisknutí myši. V předchozích verzích .NET Framework neexistovaly.
-Fokus klávesnice na přepínačích je nyní viditelný. V předchozích verzích .NET Framework nebyl.
-<xref:System.Windows.Controls.DataGrid>Sloupec CheckBox ovládacího prvku nyní používá očekávané barvy pro zpětnou vazbu fokusu klávesnice. V předchozích verzích .NET Framework neexistovaly.
-vizuály fokusu klávesnice jsou teď viditelné v <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox> ovládacích prvcích a. V předchozích verzích .NET Framework nebyl.</p>
**Vylepšení interakce čtečky obrazovky**
<ul><li><xref:System.Windows.Controls.Expander>ovládací prvky jsou nyní správně ohlášeny jako skupiny (rozbalení či sbalení) pomocí nástrojů pro čtení obrazovky.
- <xref:System.Windows.Controls.DataGridCell>ovládací prvky jsou nyní správně ohlášeny jako buňka datové mřížky (lokalizované) čtečkami obrazovky.
-Čtečky obrazovky teď budou oznamovat název, který lze upravovat <xref:System.Windows.Controls.ComboBox> .
- <xref:System.Windows.Controls.PasswordBox>ovládací prvky již nejsou oznámeny, protože &quot; čtečky obrazovky neobsahují žádné položky &quot; .</p>
**Podpora LiveRegion** Čtečky obrazovky, jako je Narrator, pomohou lidem zjistit obsah uživatelského rozhraní aplikace, obvykle tím, že popisují něco o aktuálně zaměřeném uživatelském rozhraní, protože je pravděpodobné, že je prvkem největší zájem na uživatele. Pokud se však prvek uživatelského rozhraní na obrazovce změní někam a nemá fokus, uživatel nemusí být informován o důležitých informacích a nemusí být k dispozici. LiveRegions jsou určeny k vyřešení tohoto problému. Vývojář je může použít k informování čtečky obrazovky nebo jakéhokoliv jiného klienta [automatizace uživatelského rozhraní](~/docs/framework/ui-automation/ui-automation-overview.md) , že došlo k důležité změně v prvku uživatelského rozhraní. Čtečka obrazovky pak může rozhodnout, jak a kdy se má uživatel informovat o této změně. Vlastnost LiveSetting také umožňuje, aby čtečka obrazovky věděla, jak důležité je informovat uživatele o změně provedené v uživatelském rozhraní.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.1 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Zaměřte se na .NET Framework 4.7.1. Toto je doporučený postup. Tyto změny přístupnosti jsou ve výchozím nastavení povolené v aplikacích WPF, které cílí na .NET Framework 4.7.1 nebo novějším.
- Výslovný se ze starší verze chování přístupnosti přidáním následujícího [přepínače AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v `<runtime>` části konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .
Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](~/docs/framework/ui-automation/ui-automation-overview.md).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
