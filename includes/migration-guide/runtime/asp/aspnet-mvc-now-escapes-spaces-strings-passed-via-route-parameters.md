### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC řídicí sekvence nyní mezery v řetězcích předaný prostřednictvím parametry trasy

|   |   |
|---|---|
|Podrobnosti|Aby bylo možné v souladu s RFC 2396 mezery v trasy cesty jsou nyní uvozeny řídicími znaky při naplňování parametry akce z trasy. Tak že <code>/controller/action/some data</code> dříve odpovídá trase <code>/controller/action/{data}</code> a poskytují <code>some data</code> jako parametr data, se teď poskytují <code>some%20data</code> místo.|
|Návrh|Kód by měl aktualizovat, aby unescape parametry řetězce z trasy. V případě potřeby původní identifikátor URI lze přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString rozhraní API.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

