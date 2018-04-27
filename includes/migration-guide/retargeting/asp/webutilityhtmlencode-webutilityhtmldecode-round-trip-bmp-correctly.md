### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode a odezvy BMP WebUtility.HtmlDecode správně

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí na rozhraní .NET Framework 4.5, znaky, které jsou mimo round-trip základní vícejazyčné roviny (BMP) správně, pokud jsou předány <xref:System.Net.WebUtility.HtmlDecode(System.String)> metody.|
|Návrh|Tato změna by měl mít žádný vliv na aktuální aplikace, ale chcete obnovit původní, nastavte <code>targetFramework</code> atribut <code>&lt;httpRuntime&gt;</code> element na řetězec, jinak než &quot;4.5&quot;. Můžete také nastavit <code>unicodeEncodingConformance</code> a <code>unicodeDecodingConformance</code> atributy <code>&lt;webUtility&gt;</code> konfigurační prvek za účelem řízení nezávisle na cílové verzi rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|

