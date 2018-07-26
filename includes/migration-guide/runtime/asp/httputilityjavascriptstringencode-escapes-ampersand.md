### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>Řídicí sekvence ampersand HttpUtility.JavaScriptStringEncode

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> řídicí sekvence ampersand (&amp;) znaků.|
|Návrh|Pokud vaše aplikace závisí na předchozím chování této metody, můžete přidat nastavení ASPNET: javascriptdonotencodeampersand [prvku ASP.NET appSettings](https://msdn.microsoft.com/library/hh975440.aspx) v konfiguračním souboru.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

