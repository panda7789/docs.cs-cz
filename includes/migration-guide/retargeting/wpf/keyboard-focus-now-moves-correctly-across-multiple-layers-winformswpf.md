---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614604"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>Fokus klávesnice se teď přesouvá správně napříč několika vrstvami hostování WinForms nebo WPF.

#### <a name="details"></a>Podrobnosti

Zvažte použití aplikace WPF hostující ovládací prvek WinForms, který zase hostuje ovládací prvky WPF. Pokud je jako první nebo poslední ovládací prvek v této vrstvě WPF, uživatelé nemusí být schopni kartu vymezit z vrstvy WinForms `System.Windows.Forms.Integration.ElementHost` . Tato změna opravuje tento problém a uživatelé teď mohou z vrstvy WinForms karet vymezit. Automatizované aplikace, které spoléhají na fokus bez použití uvozovacích znaků vrstvy WinForms, nemusí nadále fungovat podle očekávání.

#### <a name="suggestion"></a>Návrh

Vývojář, který chce tuto změnu využít při cílení na verzi architektury pod platformou .NET 4.7.2, může nastavit následující sadu příznaků AppContext na hodnotu false, aby bylo možné změnu povolit.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Aplikace WPF musí pro pozdější vylepšení získat výslovný souhlas se všemi vylepšeními přístupnosti v rané fázi. Jinými slovy, `Switch.UseLegacyAccessibilityFeatures` a `Switch.UseLegacyAccessibilityFeatures.2` přepínači musí být setA vývojář, který vyžaduje předchozí funkčnost při cílení na rozhraní .NET 4.7.2 nebo vyšší, může nastavit následující příznak AppContext na hodnotu true, aby se změna zakázala.

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
