---
ms.openlocfilehash: 63a38f33fef09577c5ed621727b8c38e4c7e1bdf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760851"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Výchozí algoritmus hash pro kompilátor značek pro WPF je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|WPF MarkupCompiler poskytuje služby kompilace pro soubory značek XAML.  V rozhraní .NET Framework 4.7.1 a starší verze byl použitý pro kontrolní součty výchozí hashovací algoritmus SHA1. Z poslední bezpečnostních důvodů se SHA1 toto výchozí nastavení byla změněna na SHA256 Počínaje rozhraním .NET Framework 4.7.2.  Tato změna ovlivní všechny kontrolní součet generování značek souborů během kompilace.|
|Doporučení|Jako vývojář, který cílí na .NET Framework 4.7.2 nebo vyšší a chce obnovit chování hash SHA1 musíte nastavit příznak následující AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Jako vývojář, který chce využít při cílení na určitou verzi rozhraní framework níže .NET 4.7.2 musí sady algoritmu hash SHA256 níže AppContext příznak.  Mějte na paměti, že nainstalovaná verze rozhraní .NET Framework musí být 4.7.2 nebo vyšší.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.7.2|
|Type|Změna cílení|

