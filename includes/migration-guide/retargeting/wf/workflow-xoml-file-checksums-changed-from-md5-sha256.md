---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803485"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Kontrolní součty souborů XOML pracovního postupu změněny z MD5 na SHA256

|   |   |
|---|---|
|Podrobnosti|Pro podporu ladění pracovních postupů založených na XOML pomocí sady Visual Studio je při vytváření projektů pracovních postupů obsahujících soubory XOML <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> zahrnut kontrolní součet obsahu souboru XOML v kódu generovaném jako hodnota. V rozhraní .NET Framework 4.7.2 a starších verzích tento algoritmus hash kontrolního součtu používal algoritmus MD5, který způsoboval problémy v systémech s podporou FIPS. Počínaje rozhraním .NET Framework 4.8 je použitý algoritmus SHA256. Chcete-li být kompatibilní s WorkflowMarkupSourceAttribute.MD5Digest, jsou použity pouze prvních 16 bajtů generované kontrolní součet. To může způsobit problémy při ladění. Možná budete muset znovu sestavit projekt.|
|Návrh|Pokud opětovné sestavení projektu problém nevyřeší, zkuste <code>AppContext</code> &quot;nastavit přepínač Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; na true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguračním souboru (to musí být v Souboru MSBuild.exe.config pro nástroj MSBuild.exe, který používáte):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Typ|Změna cílení|
