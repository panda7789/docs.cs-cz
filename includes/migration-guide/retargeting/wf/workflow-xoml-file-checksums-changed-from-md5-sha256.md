---
ms.openlocfilehash: f59c9f048bb3cd3f425e36b931302258fcf693f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644493"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Pracovní postup XOML souboru kontrolní součty SHA256 změnil z MD5

|   |   |
|---|---|
|Podrobnosti|V zájmu podpory ladění pracovních postupů založených na XOML pomocí sady Visual Studio, když pracovní postup projekty obsahující sestavení soubory XOML součet obsah souboru XOML je zahrnuta v kódu generovaném jako <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> hodnotu. V rozhraní .NET Framework 4.7.2 a dřívějších verzích Tento kontrolní součet hash používá algoritmus MD5, který způsobil problémy s podporou standardu FIPS v systémech. Počínaje 4.8 rozhraní .NET Framework, je použitý algoritmus SHA256. Aby s aktualizací se WorkflowMarkupSourceAttribute.MD5Digest se používají pouze prvních 16 bajtů generovaných kontrolního součtu. Může to způsobit potíže během ladění. Budete muset svůj projekt znovu sestavit.|
|Doporučení|Pokud znovu sestavení projektu problém nevyřeší, zkuste <code>AppContext</code> přepnout &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; na hodnotu true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguračním souboru (to je potřeba v souboru MSBuild.exe.config pro MSBuild.exe, který používáte):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Type|Změna cílení|
