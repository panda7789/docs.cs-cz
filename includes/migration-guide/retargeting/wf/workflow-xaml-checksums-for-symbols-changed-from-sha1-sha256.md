---
ms.openlocfilehash: 9c54572b8dcedaa103db8503cfc1155b4698c3ed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803452"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Pracovní postup XAML kontrolních součtů pro symboly změnil z SHA1, SHA256

|   |   |
|---|---|
|Podrobnosti|V zájmu podpory ladění pomocí sady Visual Studio generuje modul runtime pracovního postupu kontrolního součtu souboru XAML pracovního postupu pomocí algoritmu hash. V rozhraní .NET Framework 4.6.2 a starší verze pracovního postupu kontrolní součet hash používá algoritmus MD5, který způsobil problémy s podporou standardu FIPS v systémech. Od verze rozhraní .NET Framework 4.7, byla změněna výchozí algoritmus SHA1. Počínaje 4.8 rozhraní .NET Framework, byla změněna výchozí algoritmus SHA256.|
|Doporučení|Pokud váš kód je možné načíst instance pracovního postupu nebo vyhledejte odpovídající symboly z důvodu selhání kontrolního součtu, zkuste <code>AppContext</code> přepnout &quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; na hodnotu true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguraci:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.8|
|type|Změna cílení|

