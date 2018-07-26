### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>Formuláře Windows pro domény upbutton a downbutton akce jsou teď synchronizovaný

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozí verze <xref:System.Windows.Forms.DomainUpDown> ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce je ignorována, pokud je k dispozici text ovládacího prvku a vývojáře je potřeba použít <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce na ovládací prvek před použitím <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akce. Od verze rozhraní .NET Framework 4.7.2 i <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce v tomto scénáři pracovat nezávisle a zůstávají synchronizované.|
|Návrh|Aby aplikace využívat tyto změny, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější. Aplikace mohou těžit z těchto změn v některém z následujících způsobů:<ul><li>Ji znovu zkompilovat cíleny na rozhraní.NET Framework 4.7.2. Tato změna je ve výchozím nastavení cíleny na rozhraní.NET Framework 4.7.2 aplikací Windows Forms pro povolená nebo novější.</li><li>Požádá o ze starší verze posouvání chování přidáním následujícího kódu [přepínač AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) k <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace a nastavení na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

