---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639442"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>Výběr textu TextBox/PasswordBox WPF nedodržuje systémové barvy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozími verzemi, WPF <code>System.Windows.Controls.TextBox</code> a <code>System.Windows.Controls.PasswordBox</code> může pouze vykreslit výběr textu ve vrstvě doplněk pro úpravy. V některých motivy systému to by occlude textu, což ztěžuje ke čtení.  V rozhraní .NET Framework 4.7.2 a novějšími, vývojáři mají možnost povolení schéma vykreslování výběr nezaložené doplněk pro úpravy, které řeší tento problém.|
|Doporučení|Jako vývojář, který chce využít tato změna musí nastavit následující příznak AppContext odpovídajícím způsobem.  Chcete-li tuto funkci využít, musí být nainstalovaná verze rozhraní .NET Framework 4.7.2 nebo vyšší. Chcete-li povolen výběr nezaložené doplněk pro úpravy, použijte následující AppContext příznak.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|
