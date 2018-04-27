### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute exportuje jako ObsoleteAttribute i DeprecatedAttribute v souboru WinMD scénáře

|   |   |
|---|---|
|Podrobnosti|Když vytvoříte knihovnu metadat Windows (soubor .winmd), <xref:System.ObsoleteAttribute?displayProperty=name> atribut se exportuje jako obě <xref:System.ObsoleteAttribute?displayProperty=name> a [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Návrh|Rekompilace existujícím zdrojovém kódu, který používá <xref:System.ObsoleteAttribute?displayProperty=name> atribut může generovat upozornění při využívání tohoto kódu z jazyka C + +/ CX nebo JavaScript.We nedoporučujeme použití obě <xref:System.ObsoleteAttribute?displayProperty=name> a [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kód v spravovaná sestavení; může vést k sestavení upozornění.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Změna orientace|

