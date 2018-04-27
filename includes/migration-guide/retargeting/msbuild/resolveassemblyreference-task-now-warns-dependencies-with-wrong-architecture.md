### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Resolveassemblyreference – úloha teď upozorňuje na závislosti s nesprávnou architektura

|   |   |
|---|---|
|Podrobnosti|Úloha vydá upozornění, MSB3270, který označuje, že odkaz nebo veškeré její závislé neodpovídá architektuře aplikace. Například k tomu dochází-li aplikaci, která bylo kompilováno s <code>AnyCPU</code> možnost zahrne x86 odkaz. Takové situaci v důsledku může dojít k selhání aplikace za běhu (v takovém případě pokud je aplikace nasazená jako x64 proces).|
|Návrh|Existují dvě oblasti dopadu:<ul><li>Rekompilace generuje upozornění, které nezobrazí, když aplikace byl přeložen v předchozí verzi nástroje MSBuild. Ale protože upozornění identifikuje možné zdroj selhání běhového prostředí, je by měl být zkoumaná a řešit.</li><li>Pokud upozornění jsou považovány za chyby, aplikace se nezdaří zkompilovat.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Změna orientace|

