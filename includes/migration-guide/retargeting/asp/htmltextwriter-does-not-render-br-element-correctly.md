### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter nevykresluje `<br/>` element správně

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6, volání <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> a <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> s <code>&lt;BR /&gt;</code> prvek se vloží správně pouze jeden <code>&lt;BR /&gt;</code> (místo dvou)|
|Doporučení|Pokud aplikace závisí na nadbytečné <code>&lt;BR /&gt;</code> značky, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> by měla být volána podruhé. Všimněte si, že tato změna chování ovlivní pouze aplikace, které cílí rozhraní .NET Framework 4.6 nebo novější, takže další možnost je k cílení na předchozí verzi rozhraní .NET Framework zajistí staré chování.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

