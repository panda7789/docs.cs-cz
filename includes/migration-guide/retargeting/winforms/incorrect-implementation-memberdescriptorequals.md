### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Nesprávné implementace MemberDescriptor.Equals

|   |   |
|---|---|
|Podrobnosti|Původní implementace &quot;rovná&quot; metoda byla porovnání dvou různých řetězec vlastnosti objektů v porovnání: název kategorie popis řetězec. Potíže se má porovnat &quot;kategorie&quot; z první objekt k &quot;kategorie&quot; typu, druhý a &quot;popis&quot; k &quot;popis&quot;. Hodnota konfigurace MemberDescriptorEqualsReturnsFalseIfEquivalent můžete nastavit na hodnotu true pro vyjádření výslovného nesouhlasu nové chování, pokud cílení 4.6.2 nebo na hodnotu false, chcete-li povolit tuto opravu, při cílení na verzi framework je nižší než 4.6.2.|
|Návrh|Pokud je aplikace závislá na MemberDescriptor.Equals někdy vrácení hodnoty false při popisovače jsou ekvivalentní a cílení 4.6.2 verze rozhraní .NET Framework, máte několik možností:<ol><li>Provádět změny kódu k porovnání &quot;kategorie&quot; a &quot;popis&quot; pole ručně kromě spuštění metody Equals.</li><li>Odhlásit se z této změny přidáním následující hodnotu do souboru app.config:</li></ol><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cíle 4.6.1 nebo nižší verze rozhraní .NET Framework a chcete tuto změnu povolená, můžete nastavit kompatibility přepínače na hodnotu false přidáním následující hodnotu do souboru app.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

