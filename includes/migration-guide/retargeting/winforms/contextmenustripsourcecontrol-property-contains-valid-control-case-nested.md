### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>Vlastnost ContextMenuStrip.SourceControl obsahuje platný ovládací prvek v případě vnořených ToolStripMenuItems

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozí verze <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost nesprávně vrátí hodnotu null, když uživatel otevře nabídku z vnořené <xref:System.Windows.Forms.ToolStripMenuItem> ovládacích prvků. V rozhraní .NET Framework 4.7.2 a novějších verzích <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> vlastnost je vždycky nastavený na skutečný zdroj ovládacího prvku.|
|Návrh|<strong>Jak aktivování nebo zrušení těchto změn</strong>aby aplikace využívat tyto změny, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější. Aplikace mohou těžit z těchto změn v některém z následujících způsobů:<ul><li>To cílí na .NET Framework 4.7.2. Tato změna je ve výchozím nastavení cíleny na rozhraní.NET Framework 4.7.2 aplikací Windows Forms pro povolená nebo novější.</li><li>Cílí na rozhraní .NET Framework 4.7.1 nebo starší verzi a výslovný chování starších verzí usnadnění přidáním následujícího kódu [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> část souboru app.config a nastavíte ho na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které se zaměřují na rozhraní .NET Framework 4.7.2 nebo novější a chcete zachovat starší chování můžete přejít k využívání staršího zdrojového hodnoty ovládacího prvku explicitním nastavením na tento přepínač AppContext <code>true</code>.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

