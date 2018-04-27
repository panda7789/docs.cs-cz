### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nevykresluje `<br/>` element správně

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s <code>&lt;BR /&gt;</code> element správně vloží pouze jeden <code>&lt;BR /&gt;</code> (namísto dvě)|
|Návrh|Pokud aplikace závisí na nadbytečné <code>&lt;BR /&gt;</code> štítku <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> by měla být volána ještě jednou. Všimněte si, že tato změna chování ovlivní pouze aplikace cílených na rozhraní .NET Framework 4.6 nebo novější, takže další možnost je cíle předchozí verzi rozhraní .NET Framework zajistí, že původní chování.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

