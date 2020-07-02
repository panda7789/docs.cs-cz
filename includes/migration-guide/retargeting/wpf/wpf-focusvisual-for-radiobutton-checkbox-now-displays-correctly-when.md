---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614613"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a>WPF FocusVisual pro RadioButton a CheckBox se teď zobrazí správně, když ovládací prvky nemají žádný obsah.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a starších verzích, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> jsou nekonzistentní a v klasických a vysoký kontrastch motivech jsou nesprávné vizuály fokusu.  K těmto problémům dochází v případech, kdy ovládací prvky nemají sadu obsahu.  To může zjednodušit přechod mezi motivy a označit vizuál jako fokus. V .NET Framework 4.7.2 jsou teď tyto vizuály v různých motivech konzistentní a snadněji viditelné v klasických a Vysoký kontrastch motivech.

#### <a name="suggestion"></a>Návrh

Vývojář cílící .NET Framework 4.7.2, který se chce vrátit k chování v .NET 4.7.1, bude muset nastavit následující příznak AppContext.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Vývojář, který chce tuto změnu využít při cílení na verzi architektury pod platformou .NET 4.7.2, musí nastavit následující příznaky AppContext. Všimněte si, že všechny příznaky musí být správně nastaveny a nainstalovaná verze .NET Framework musí být 4.7.2 nebo vyšší. Aby bylo možné získat nejnovější vylepšení, je nutné, aby aplikace WPF měly výslovný souhlas se všemi předchozími vylepšeními usnadnění. Chcete-li to provést, zajistěte, aby přepínače AppContext přepínače ' Switch. UseLegacyAccessibilityFeatures ' a ' Switch. UseLegacyAccessibilityFeatures. 2 ' byly nastaveny na hodnotu false.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
