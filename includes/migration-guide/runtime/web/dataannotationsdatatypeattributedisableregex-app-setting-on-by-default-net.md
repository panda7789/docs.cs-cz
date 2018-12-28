### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>nastavení aplikace, které "dataAnnotations:dataTypeAttribute:disableRegEx" je ve výchozím v rozhraní .NET Framework 4.7.2

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.1, nastavení aplikace (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) byl zaveden, který umožňuje uživatelům zakázat použití regulárních výrazů v atributech typu dat (například <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, a <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). To pomáhá snížit ohrožení zabezpečení, jako je například vyhnout možnosti útoku DOS pomocí konkrétní regulární výrazy.<br/>V rozhraní .NET Framework 4.6.1, tato nastavení aplikace zakážete použití regulárního výrazu bylo nastavené na <code>false</code> ve výchozím nastavení. Rovnou začít tématem rozhraní .NET Framework 4.7.2, tato konfigurace přepínač nastavený na <code>true</code> ve výchozím nastavení k dalšímu snížení zabezpečení ohrožení zabezpečení pro webové aplikace, které jsou cíleny na rozhraní .NET Framework 4.7.2 a vyšší.|
|Doporučení|Pokud zjistíte, že regulární výrazy ve webové aplikaci po upgradu na rozhraní .NET Framework 4.7.2 nefungují, můžete aktualizovat hodnotu <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> nastavení <code>false</code> se vrátit k předchozí chování.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Modul runtime|

