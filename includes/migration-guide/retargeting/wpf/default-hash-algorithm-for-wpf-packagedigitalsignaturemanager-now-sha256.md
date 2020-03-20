---
ms.openlocfilehash: 141e906077748795e0360cec450a54a9fd170dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858980"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Výchozí algoritmus hash pro WPF PackageDigitalSignatureManager je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|Poskytuje <code>System.IO.Packaging.PackageDigitalSignatureManager</code> funkce pro digitální podpisy ve vztahu k wpf balíčky.  V rozhraní .NET Framework 4.7 a starších<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>verzích byl výchozí algoritmus ( ) použitý pro podepisování částí balíčku SHA1.  Z důvodu nedávných obav o zabezpečení sha1, toto výchozí bylo změněno na SHA256 počínaje rozhraním .NET Framework 4.7.1.  Tato změna ovlivní všechny podepisování balíčků, včetně dokumentů XPS.|
|Návrh|Vývojář, který chce využít tuto změnu při cílení na verzi rozhraní framework pod rozhraním .NET Framework 4.7.1 nebo vývojáře, který vyžaduje předchozí funkce při cílení na rozhraní .NET Framework 4.7.1 nebo vyšší, může správně nastavit následující příznak AppContext.  Hodnota true bude mít za následek SHA1 se používá jako výchozí algoritmus; falešné výsledky v SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|
