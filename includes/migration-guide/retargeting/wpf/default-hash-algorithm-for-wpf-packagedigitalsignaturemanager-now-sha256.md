### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Výchozí algoritmus hash pro WPF PackageDigitalSignatureManager je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> Poskytuje funkce pro digitální podpisy ve vztahu k WPF balíčky.  V rozhraní .NET Framework 4.7 a předchozími verzemi, je výchozí algoritmus (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) pro podpis součástí balíčku byl SHA1.  Z poslední bezpečnostních důvodů se SHA1 byl změněn na SHA256 toto výchozí nastavení od verze rozhraní .NET Framework 4.7.1.  Tato změna ovlivní všechny podepisování balíčků, včetně dokumentů XPS.|
|Návrh|Vývojář, který chce využít tato změna při cílení na určitou verzi rozhraní framework pod .NET Framework 4.7.1 nebo vývojář, který vyžaduje předchozí funkce při cílení na rozhraní .NET Framework 4.7.1 nebo vyšší můžete nastavit následující příznak AppContext odpovídajícím způsobem.  Hodnota true způsobí SHA1 používá jako výchozí algoritmus; false výsledkem SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|

