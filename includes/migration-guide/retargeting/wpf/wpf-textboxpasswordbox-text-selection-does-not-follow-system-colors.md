---
ms.openlocfilehash: 649e4456ef6a11903ab1b390baf56583f31f5562
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760840"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Výběr textu TextBox/PasswordBox WPF nedodržuje systémové barvy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozími verzemi, WPF <code>System.Windows.Controls.TextBox</code> a <code>System.Windows.Controls.PasswordBox</code> může pouze vykreslit výběr textu ve vrstvě doplněk pro úpravy. V některých motivy systému to by occlude textu, což ztěžuje ke čtení.  V rozhraní .NET Framework 4.7.2 a novějšími, vývojáři mají možnost povolení schéma vykreslování výběr nezaložené doplněk pro úpravy, které řeší tento problém.|
|Doporučení|Jako vývojář, který chce využít tato změna musí nastavit následující příznak AppContext odpovídajícím způsobem.  Chcete-li tuto funkci využít, musí být nainstalovaná verze rozhraní .NET Framework 4.7.2 nebo vyšší. Chcete-li povolen výběr nezaložené doplněk pro úpravy, použijte následující AppContext příznak.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|

