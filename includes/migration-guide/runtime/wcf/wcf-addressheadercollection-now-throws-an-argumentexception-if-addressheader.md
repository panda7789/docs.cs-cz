### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>WCF AddressHeaderCollection nyní způsobí výjimku, ArgumentException – Pokud element do objektu addressHeader má hodnotu null

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> konstruktor vyvolá <xref:System.ArgumentException> Pokud jeden z elementů je <code>null</code>. V rozhraní .NET Framework 4.7 a starší verze je vyvolána žádná výjimka.|
|Návrh|Pokud narazíte na problémy s kompatibilitou se tato změna na rozhraní .NET Framework 4.7.1 nebo novější, můžete můžete výslovný nesouhlas s jeho přidáním následující řádek na <code>&lt;runtime&gt;</code> v souboru app.config::<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|

