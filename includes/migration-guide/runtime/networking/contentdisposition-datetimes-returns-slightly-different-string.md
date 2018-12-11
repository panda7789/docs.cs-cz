### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>Vrátí řetězec mírně liší, ContentDisposition data a času

|   |   |
|---|---|
|Podrobnosti|Řetězcových reprezentací objektu <xref:System.Net.Mime.ContentDisposition?displayProperty=name>společnosti byly aktualizovány, počínaje 4.6, vždy představující hodinu součást <xref:System.DateTime?displayProperty=name> se dvěma číslicemi. Toto je v souladu s [RFC822](http://www.ietf.org/rfc/rfc0822.txt) a [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). To způsobí, že <xref:System.Net.Mime.ContentDisposition.ToString> vrátit řetězec mírně liší v 4.6 ve scénářích prvků času dispozice byl před 10:00:00. Všimněte si, že ContentDispositions serializují někdy prostřednictvím převádění na řetězce, tak, aby <xref:System.Net.Mime.ContentDisposition.ToString> operace, serializace nebo GetHashCode volání byste měli zkontrolovat.|
|Doporučení|Nečekejte, že se mezi sebou správně porovnání řetězcové reprezentace ContentDispositions z různých verzí rozhraní .NET Framework. Převod řetězce ContentDispositions, pokud je to možné, před provedením porovnání.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

