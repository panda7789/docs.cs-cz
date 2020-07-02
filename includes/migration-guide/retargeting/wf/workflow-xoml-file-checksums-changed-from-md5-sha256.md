---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616240"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Kontrolní součty souborů XOML pracovního postupu se změnily z MD5 na SHA256

#### <a name="details"></a>Podrobnosti

Aby bylo možné podporovat ladění pracovních postupů na základě souborů XOML pomocí sady Visual Studio, jsou při vytváření projektů pracovních postupů obsahujících soubory XOML kontrolní součet obsahu souboru XOML obsažen v kódu generovaném jako <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> hodnota. V .NET Framework 4.7.2 a dřívějších verzích tato kontrolní hodnota hash použila algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS. Počínaje .NET Framework 4,8 se používá algoritmus SHA256. Aby bylo možné compatibile pomocí WorkflowMarkupSourceAttribute. MD5Digest, jsou použity pouze prvních 16 bajtů vygenerovaného kontrolního součtu. To může způsobit problémy při ladění. Možná budete muset projekt znovu sestavit.

#### <a name="suggestion"></a>Návrh

Pokud znovu sestavíte projekt, zkuste nastavit `AppContext` přepínač &quot;Switch.System. Workflow. ComponentModel. UseLegacyHashForXomlFileChecksum &quot; na hodnotu true. V kódu:

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

Nebo v konfiguračním souboru (musí být MSBuild.exe.config pro MSBuild.exe, které používáte):

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,8         |
| Typ    | Změna cílení |
