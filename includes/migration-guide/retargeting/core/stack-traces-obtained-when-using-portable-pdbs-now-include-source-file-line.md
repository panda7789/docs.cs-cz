---
ms.openlocfilehash: 384f8c7fa08b69c13d05edb3404787d428dad837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639425"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Trasování zásobníku, které získáte při použití souborům portable PDB nyní zahrnují informace o zdrojovém souboru a řádku, pokud o to požádá

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.2, trasování zásobníku, které získáte při použití souborům portable PDB obsahovat zdrojového souboru a řádku informace na požádání. Ve verzích před rozhraní .NET Framework 4.7.2, zdrojového souboru a řádku by být informace není k dispozici při použití souborům portable PDB i v případě, že explicitně vyžádány.|
|Doporučení|Pro aplikace, které se zaměřují na rozhraní .NET Framework 4.7.2, můžete zrušit informace zdrojového souboru a řádku při použití přenosných souborů pdb, pokud není žádoucí, přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>U aplikací určených pro starší verze rozhraní .NET Framework ale spustit v rozhraní .NET Framework 4.7.2 nebo později, můžete přejít do zdrojového souboru a řádku informace při použití přidáním následujícího kódu k souborům portable PDB <code>&lt;runtime&gt;</code> část vaší <code>app.config</code>souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|
