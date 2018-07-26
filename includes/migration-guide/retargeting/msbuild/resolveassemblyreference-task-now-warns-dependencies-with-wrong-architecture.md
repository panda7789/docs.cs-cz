### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Resolveassemblyreference – úloha teď upozorňuje na závislosti pomocí nesprávného architektury

|   |   |
|---|---|
|Podrobnosti|Úloha vysílá varování, MSB3270, což znamená, že odkaz nebo některá z jejích závislostí neodpovídá architektuře aplikace. Například dochází k tomu, který byl zkompilován pomocí aplikace <code>AnyCPU</code> x x86 zahrnuje možnost odkaz. Takový scénář může vést k selhání aplikace za běhu (v tomto případě v případě, že je aplikace nasazená jako x x64 proces).|
|Návrh|Existují dvě oblasti dopad na chod firmy:<ul><li>Rekompilace generuje upozornění, která se neobjevil při kompilaci aplikace v předchozí verzi nástroje MSBuild. Ale vzhledem k tomu, že toto upozornění identifikuje stávají možným zdrojem chyby, ji by měl být prozkoumat a zákazníky a vyřešené.</li><li>Pokud jsou upozornění zpracována jako chyby, aplikace se nepodaří zkompilovat.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Mění se cílení|

