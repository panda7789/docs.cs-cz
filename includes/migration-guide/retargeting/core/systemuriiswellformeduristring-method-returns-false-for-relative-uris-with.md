### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>System.Uri.IsWellFormedUriString metoda vrátí hodnotu false pro relativní identifikátory URI s dvojtečkou char v první segment

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> bude považovat relativní identifikátory URI s <code>:</code> v jejich první segment, protože není ve správném formátu. Jedná se o změnu z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> chování v rozhraní .NET Framework 4.0, který byl proveden tak, aby odpovídala RFC3986.|
|Návrh|Tato změna (jako je mnoho dalších změn URI) ovlivní pouze aplikace cílený na rozhraní .NET Framework 4.5 (nebo novější). Chcete-li dál používat staré chování, určete aplikaci pro rozhraní .NET Framework 4.0. Alternativně kontrolovat URI před voláním <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> hledá <code>:</code> znaky, které můžete chtít odebrat pro účely ověření, pokud je původní chování žádoucí.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

