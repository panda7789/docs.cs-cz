### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged událostí a SelectedContent vlastnost

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, <xref:System.Windows.Controls.TabControl> aktualizuje hodnotu jeho <xref:System.Windows.Controls.TabControl.SelectedContent> vlastnost než se vyvolá <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> událost, když se změní jeho výběr. V rozhraní .NET Framework 4.7 a starší verze aktualizace, která se SelectedContent došlo po události.|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější můžete zamítnutí to změnit a použijte starší verze chování přidáním následujícího <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.7 nebo dřívější ale běží na rozhraní .NET Framework 4.7.1 nebo později můžete povolit nové chování přidáním následující řádek do <code>&lt;runtime&gt;</code> části souboru .configuration aplikace:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

