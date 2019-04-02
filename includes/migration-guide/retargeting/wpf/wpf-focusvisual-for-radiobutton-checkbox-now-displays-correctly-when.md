---
ms.openlocfilehash: 38c50244b1cee41bd95c232ac5d1691c59c55488
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760846"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>Zobrazí FocusVisual WPF pro přepínače a zaškrtávacího políčka nyní správně při ovládací prvky nemají žádný obsah

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozími verzemi, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> mají nekonzistentní a v modelu Classic a Vysoký kontrast motivy, nesprávné fokus vizuály.  Těmto problémům dochází v případech, ve kterém ovládací prvky nemají žádné sadu obsahu.  Přechod mezi motivy matoucí a vizuál se fokus může být špatně vidět. V rozhraní .NET Framework 4.7.2 tyto vizuály jsou teď víc konzistentní v rámci celého motivy a snadněji viditelné v modelu Classic a Vysoký kontrast – motivy.|
|Doporučení|Vývojář cílí na rozhraní .NET Framework 4.7.2, který chcete vrátit k chování v prostředí .NET 4.7.1 muset nastavit příznak následující AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Jako vývojář, který chce využít tato změna při cílení na určitou verzi rozhraní framework níže .NET 4.7.2 musí nastavit následující příznaky AppContext. Mějte na paměti, že všechny příznaky musí být nakonfigurovaná a nainstalovaná verze rozhraní .NET Framework musí být 4.7.2 nebo vyšší. Aplikace WPF je potřeba povolit všechny dřívější vylepšení přístupnosti zobrazíte nejnovější vylepšení. Chcete-li to provést, ujistěte se, že oba AppContext přepínače "Switch.UseLegacyAccessibilityFeatures" a "Switch.UseLegacyAccessibilityFeatures.2" jsou nastavena na hodnotu false.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|

