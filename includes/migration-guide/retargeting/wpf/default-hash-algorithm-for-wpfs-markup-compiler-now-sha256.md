### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>Výchozí algoritmus hash pro kompilátoru značek na WPF je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|WPF MarkupCompiler poskytuje služby kompilace pro soubory XAML značek.  V rozhraní .NET Framework 4.7.1 a starší verze se používá pro kontrolní součty výchozí algoritmus hash SHA1. Z důvodu poslední aspekty zabezpečení s SHA1 toto výchozí nastavení se změnil na SHA256 od verze rozhraní .NET Framework 4.7.2.  Tato změna ovlivňuje všechny kontrolní součet generování značek souborů během kompilace.|
|Návrh|Vývojáři, který cílí rozhraní .NET Framework 4.7.2 nebo vyšší a chce vrátit k chování hash SHA1 musí nastavit příznak následující AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Vývojáři, který chce využívat algoritmu hash SHA256, při cílení na verzi framework pod .NET 4.7.2 musíte nastavit níže AppContext příznak.  Všimněte si, že nainstalovaná verze rozhraní .NET Framework musí být 4.7.2 nebo vyšší.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.7.2|
|Typ|Změna orientace|

