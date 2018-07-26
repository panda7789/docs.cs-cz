### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>Vlastnost HttpRequest.ContentEncoding zakazuje UTF7

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, kódování UTF-7 je zakázáno v <xref:System.Web.HttpRequest?displayProperty=name>s "subjekty. Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.|
|Návrh|V ideálním případě by měl používat v kódování UTF-7 aktualizují aplikace <xref:System.Web.HttpRequest?displayProperty=name>s. Alternativně lze obnovit starší chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atribut [appSettings](https://msdn.microsoft.com/library/hh975440(v=vs.110).aspx) elementu.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

