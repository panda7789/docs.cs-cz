---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859237"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current může vrátit null při volání v using klauzule

|   |   |
|---|---|
|Podrobnosti|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>může <code>null</code> dojít <xref:System.NullReferenceException> k návratu, pokud jsou splněny všechny následující podmínky:<ul><li>Načtete hodnotu <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> vlastnosti v metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</li><li>Konkretizovat <xref:System.ServiceModel.OperationContextScope> objekt <code>using</code> v klauzuli.</li><li>Načtete hodnotu <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> vlastnosti <code>using statement</code>v rámci . Například:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Návrh|Chcete-li tento problém vyřešit, můžete provést následující kroky:<ul><li>Upravte kód takto, abyste nastořel i nový objekt bez objektu:<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A></li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Nainstalujte nejnovější aktualizaci rozhraní .NET Framework 4.6.2 nebo upgradujte na novější verzi rozhraní .NET Framework. Tím se zakáže <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> tok in a obnoví chování wcf aplikací v rozhraní .NET Framework 4.6.1 a starší verze. Toto chování je konfigurovatelné; je ekvivalentní přidání následujícího nastavení aplikace do konfiguračního souboru:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Pokud tato změna je nežádoucí a vaše aplikace závisí na kontextu spuštění protékající mezi kontexty operace, můžete povolit jeho tok takto:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|
