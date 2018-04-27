### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition data a času vrátí mírně odlišné řetězec

|   |   |
|---|---|
|Podrobnosti|Řetězec reprezentace <xref:System.Net.Mime.ContentDisposition?displayProperty=name>společnosti byly aktualizovány, od verze 4.6, vždy představující hodinu komponenta <xref:System.DateTime?displayProperty=name> s dvě číslice. Toto nastavení slouží k dosažení souladu s [RFC822](http://www.ietf.org/rfc/rfc0822.txt) a [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). To způsobí, že <xref:System.Net.Mime.ContentDisposition.ToString> vrátit mírně odlišné řetězec v 4.6 ve scénářích, kde jeden z elementů čas dispozice byl před 10:00 AM. Všimněte si, že jsou ContentDispositions někdy serializovat prostřednictvím jejich převádění na řetězce, tak, aby <xref:System.Net.Mime.ContentDisposition.ToString> by měl být zkontrolovány operace, serializace nebo GetHashCode volání.|
|Návrh|Nečekejte, že bude řetězec reprezentace ContentDispositions z různých verzí rozhraní .NET Framework správně porovnat jednu na druhou. Převod řetězce ContentDispositions, pokud je to možné, před provedením porovnání.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

