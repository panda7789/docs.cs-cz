### <a name="resizing-a-grid-can-hang"></a>Změna velikosti mřížka může na

|   |   |
|---|---|
|Podrobnosti|Nekonečná smyčka může dojít během rozložení <code>T:System.Windows.Controls.Grid</code> podle následujících okolností:<ul><li>Definice řádků obsahovat dvě *-řádků, jak deklarace MinHeight a MaxHeight.</li><li>Obsah *-řádky nepřekročí odpovídající MaxHeight</li><li>K dispozici výška mřížky dojde k překročení první MinHeight (plus jakékoliv pevné nebo automaticky řádky)</li><li>Aplikace rozhraní .NET Framework 4.7 cílí nebo vyjádřit výslovný souhlas pro algoritmus 4.7 přidělení nastavením <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>Smyčky by také mohlo dojít s více než dva řádky nebo v případě podobá pro sloupce. Je problém vyřešen v rozhraní .NET Framework 4.7.1.|
|Návrh|Upgrade na rozhraní .NET Framework 4.7.1.  Případně pokud nepotřebujete algoritmus 4.7 přidělení můžete použít následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|

