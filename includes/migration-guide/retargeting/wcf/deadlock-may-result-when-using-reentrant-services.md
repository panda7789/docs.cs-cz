### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zablokování může dojít, pokud používáte vícenásobné služby

|   |   |
|---|---|
|Podrobnosti|Zablokování může způsobit vícenásobné služby, který omezuje instancí služby na jedno vlákno provádění najednou. Služby, které jsou náchylné k tomuto problému dojde, bude mít následující <xref:System.ServiceModel.ServiceBehaviorAttribute> v jejich kódu:<pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Návrh|Chcete-li vyřešit tento problém, můžete provést následující:<ul><li>Nastavte režim služby souběžnosti na <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> nebo &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Příklad:</li></ul><pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Nainstalujte nejnovější aktualizace pro rozhraní .NET Framework 4.6.2 nebo upgrade na novější verzi rozhraní .NET Framework. To zakáže tok <xref:System.Threading.ExecutionContext> v <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. Toto chování je možné konfigurovat; je ekvivalentní k přidání následujících nastavení aplikace do konfiguračního souboru:</li></ul><pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&#13;&#10;The value of &#39;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&#39; should never be set to &#39;false&#39; for Rentrant services.&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|

