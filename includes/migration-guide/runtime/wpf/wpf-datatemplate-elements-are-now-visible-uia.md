### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>WPF DataTemplate elementy jsou nyní viditelné pro UIA

|   |   |
|---|---|
|Podrobnosti|Dříve <xref:System.Windows.DataTemplate?displayProperty=name> elementy byly neviditelná pro automatizaci uživatelského rozhraní. Od verze 4.5, zjistí automatizace uživatelského rozhraní těchto elementů. To je užitečné v mnoha případech ale může dojít k narušení testy, které jsou závislé na modelu UIA stromy neobsahující <xref:System.Windows.DataTemplate?displayProperty=name> elementy.|
|Návrh|Testy automatizace uživatelského rozhraní pro tuto aplikaci může být nutné aktualizovat, aby účet pro strom UIA teď včetně dříve neviditelná <xref:System.Windows.DataTemplate?displayProperty=name> elementy. Nyní může například testy, které očekávají některé prvky, které chcete vedle sebe nutné očekávat dříve neviditelné prvky UIA mezi nimi. Nebo testy, které jsou závislé na určitých počty nebo indexů pro elementy UIA může být nutné aktualizovat s novými hodnotami.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|

