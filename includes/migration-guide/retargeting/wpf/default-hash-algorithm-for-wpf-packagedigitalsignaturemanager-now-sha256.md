### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Výchozí algoritmus hash pro WPF PackageDigitalSignatureManager je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> Poskytuje funkce pro digitální podpisy ve vztahu k WPF balíčky.  V rozhraní .NET Framework 4.7 a starší verze, výchozí algoritmus (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) používá k podepisování části balíčku byl SHA1.  Z důvodu poslední aspekty zabezpečení s SHA1 toto výchozí nastavení se změnil na SHA256 od verze rozhraní .NET Framework 4.7.1.  Tato změna ovlivňuje všechny balíček podepisování, včetně dokumenty XPS.|
|Návrh|Vývojáři, který chce využívat tuto změnu při cílení na verzi framework pod .NET 4.7.1 nebo vývojáři, který vyžaduje předchozí funkce při cílení na rozhraní .NET 4.7.1 nebo větší můžou nastavit příznak následující AppContext správně.  Hodnota true bude mít za následek SHA1 používán jako výchozí algoritmus; false výsledkem SHA256.<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

