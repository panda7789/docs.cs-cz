### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC řídicí sekvence nyní mezery v řetězcích předaná prostřednictvím parametry trasy

|   |   |
|---|---|
|Podrobnosti|K dosažení souladu s RFC 2396, jsou prostory v trasy cesty uvozený teď při naplňování parametry akce z trasy. Ano zatímco <code>/controller/action/some data</code> dříve odpovídá trasy <code>/controller/action/{data}</code> a zadejte <code>some data</code> jako parametr dat bude nyní poskytovat <code>some%20data</code> místo.|
|Návrh|Kód se musí aktualizovat na unescape parametrů řetězce z trasy. V případě potřeby původní URI lze přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString rozhraní API.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

