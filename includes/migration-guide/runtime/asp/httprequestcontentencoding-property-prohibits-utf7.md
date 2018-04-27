### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Vlastnost HttpRequest.ContentEncoding znemožňuje UTF7

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, kódování UTF-7 zakázané <xref:System.Web.HttpRequest?displayProperty=name>s' subjektů. Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.|
|Návrh|V ideálním případě aplikace by měla být aktualizovány nechcete použít v kódování UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s. Alternativně může být obnovena starší verze chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atribut [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) elementu.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

