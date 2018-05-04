### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>Nyní jsou synchronizované na WinForm domény upbutton a downbutton akce

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozích verzích <xref:System.Windows.Forms.DomainUpDown> ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce je ignorována, pokud je k dispozici text ovládacího prvku a vývojáře je potřeba použít <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce na ovládací prvek před použitím <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce. Od verze rozhraní .NET Framework 4.7.2 i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce nezávisle pracovat v tomto scénáři a zůstanou synchronizovány.|
|Návrh|Aby aplikace, abyste mohli využívat výhod tyto změny, musí běžet na rozhraní .NET Framework 4.7.2 nebo novější. Aplikace můžete využít tyto změny v některém z následujících způsobů:<ul><li>Ho znovu zkompiluje cílí na rozhraní .NET Framework 4.7.2. Tuto změnu je povoleno ve výchozím nastavení v aplikacích Windows Forms cílených na rozhraní .NET Framework 4.7.2 nebo novější.</li><li>Ho výslovný nesouhlas starší verze posouvání chování přidáním následující [AppContext přepínač](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> části konfiguračním souboru aplikace a jeho nastavení na hodnotu <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

