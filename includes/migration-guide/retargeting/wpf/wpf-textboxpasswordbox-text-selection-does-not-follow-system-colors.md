---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614621"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Výběr textu v grafickém rozhraní WPF/PasswordBox nedodržuje systémové barvy

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a dřívějších verzích, WPF `System.Windows.Controls.TextBox` a `System.Windows.Controls.PasswordBox` mohl by vykreslovat pouze výběr textu ve vrstvě doplňků. V některých systémových motivech by to occlude text, takže je obtížné ho přečíst.  V .NET Framework 4.7.2 a novějších mají vývojáři možnost Povolit schéma vykreslování výběru založeného na doplňku bez doplňků, které tento problém vyřeší.

#### <a name="suggestion"></a>Návrh

Vývojář, který chce využít tuto změnu, musí odpovídajícím způsobem nastavit následující příznak AppContext.  Aby bylo možné využít tuto funkci, musí být nainstalovaná verze .NET Framework 4.7.2 nebo novější. Chcete-li povolit výběr, který není založen na doplňky, použijte následující příznak AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
