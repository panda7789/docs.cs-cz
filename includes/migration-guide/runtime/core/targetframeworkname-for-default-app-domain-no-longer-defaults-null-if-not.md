### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName pro výchozí doménu aplikace už použije se výchozí hodnota null, není-li nastavit

|   |   |
|---|---|
|Podrobnosti|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Bylo dříve null ve výchozí doméně aplikace, pokud byla explicitně nastavena. Od verze 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> vlastnost pro výchozí doménu aplikace bude mít výchozí hodnotu odvozené z TargetFrameworkAttribute (Pokud je k dispozici). Domény jiné než výchozí aplikace bude dále dědit jejich <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> z výchozí domény aplikace (které nebude výchozí na hodnotu null v 4.6) Pokud není explicitně přepsána.|
|Návrh|Kód se musí aktualizovat na nezávisí na <xref:System.AppDomainSetup.TargetFrameworkName> jako výchozí bude použit na hodnotu null. Pokud se vyžaduje, aby tato vlastnost nadále vyhodnotit na hodnotu null, se může být explicitně nastaven na tuto hodnotu.|
|Rozsah|Edge|
|Version|4.6|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

