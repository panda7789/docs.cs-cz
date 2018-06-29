### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>WebUtility.HtmlDecode už dekóduje neplatný vstupních sekvencí

|   |   |
|---|---|
|Podrobnosti|Ve výchozím nastavení metody dekódování již neprovádějí dekódování neplatné vstupní sekvence do neplatného řetězce UTF-16. Namísto toho vracejí původní vstup.|
|Návrh|Změna dekodéru výstupu by měla mít vliv, pouze pokud do řetězců ukládáte binární data namísto dat UTF-16. Chcete-li toto chování explicitně řídit, nastavte <code>aspnet:AllowRelaxedUnicodeDecoding</code> atribut [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu, který chcete <code>true</code> povolit starší verze chování nebo <code>false</code> povolit aktuální chování.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|

