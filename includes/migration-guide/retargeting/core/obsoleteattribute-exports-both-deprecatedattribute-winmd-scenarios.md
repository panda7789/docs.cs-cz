### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute exportuje jako ObsoleteAttribute a DeprecatedAttribute ve scénářích WinMD

|   |   |
|---|---|
|Podrobnosti|Při vytváření knihovny metadat Windows (soubor winmd), <xref:System.ObsoleteAttribute?displayProperty=name> atribut se exportují jako <xref:System.ObsoleteAttribute?displayProperty=name> a [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Návrh|Rekompilace existující zdrojový kód, který používá <xref:System.ObsoleteAttribute?displayProperty=name> atribut může generovat upozornění při využívání tento kód v C + +/ CX nebo JavaScript.We nedoporučujeme použití obou <xref:System.ObsoleteAttribute?displayProperty=name> a [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kód ve spravovaných sestavení; může dojít v upozorněních sestavení.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Mění se cílení|

