### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Podporovat zápis speciální relativní identifikátor URI, pokud je k dispozici kódování Unicode

|   |   |
|---|---|
|Podrobnosti|<xref:System.Uri> už vyvolá výjimku <xref:System.NullReferenceException> při volání metody <xref:System.Uri.TryCreate%2A> na určité relativní identifikátory URI obsahující Unicode.The nejjednodušší reprodukovat <xref:System.NullReferenceException> je menší než, pomocí dvou příkazů ekvivalentní:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Pro reprodukci <xref:System.NullReferenceException>, musí platit následující položky:<ul><li>Identifikátor URI musí být zadán jako relativní ho s předponou ' http:' a ne její ' / /'.</li><li>Identifikátor URI musí obsahovat procent kódováním Unicode nebo nerezervované symboly.</li></ul>|
|Návrh|Místo toho by měl určovat uživatelů v závislosti na toto chování tak, aby zakázala relativní identifikátory URI <xref:System.UriKind.Absolute?displayProperty=nameWithType> při vytváření identifikátoru URI.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

