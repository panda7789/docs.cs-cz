---
ms.openlocfilehash: 2f960942bda54505690cbac3151ef74ec0ab5ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235518"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zablokování může dojít při použití služeb Reentrant

|   |   |
|---|---|
|Podrobnosti|Zablokování může mít za následek služby Reentrant, která omezuje instance služby na jedno vlákno spuštění najednou. Služby náchylné k výskytu tohoto <xref:System.ServiceModel.ServiceBehaviorAttribute> problému budou mít v kódu následující:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Návrh|Chcete-li tento problém vyřešit, můžete provést následující kroky:<ul><li>Nastavte režim souběžnosti služby <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> &lt;na system.servicemodel.concurrencyMode.Multiple?displayProperty=nameWithType&gt;. Například:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Nainstalujte nejnovější aktualizaci rozhraní .NET Framework 4.6.2 nebo upgradujte na novější verzi rozhraní .NET Framework. Tím se zakáže <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>tok in . Toto chování je konfigurovatelné; je ekvivalentní přidání následujícího nastavení aplikace do konfiguračního souboru:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Hodnota <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> by měla být <code>false</code> nikdy nastavena na služby Rentrant.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|
