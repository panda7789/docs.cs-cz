### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF rozložení zaokrouhlení okraje došlo ke změně

|   |   |
|---|---|
|Podrobnosti|Způsob, ve kterém jsou zaokrouhleny okraje a ohraničení a pozadí v nich došlo ke změně. V důsledku této změny:<ul><li>Šířky nebo výšky elementů může zvětšit nebo zmenšit o maximálně jeden bod.</li><li>Umístění objektu můžete přesunout tak, že maximálně jeden pixel.</li><li>Zarovnaný elementy lze vypnout center o maximálně jeden bod vodorovně nebo svisle.</li></ul>Ve výchozím nastavení je toto nové rozložení povolená jenom pro aplikace, které cílí na rozhraní .NET Framework 4.6.|
|Návrh|Vzhledem k tomu, že tato změna se obvykle eliminovat výstřižek pravé nebo dolní části ovládacích prvků WPF v vysoké DPIs, aplikace, které cílí na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 se můžete rozhodnout do této nové chování přidáním následující řádek na <code>&lt;runtime&gt;</code> v souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.6 ale ovládacích prvků WPF k vykreslení pomocí předchozí algoritmus rozložení, aby se to lze provést přidáním následující řádek do <code>&lt;runtime&gt;</code> v souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|

