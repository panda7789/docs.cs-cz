### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant nebo Contract.Requires<TException> Neberte v úvahu String.IsNullOrEmpty být čistě

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí .NET Framework 4.6.1, pokud invariantní smlouvu aktivoval pro <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> nebo předběžné podmínky smlouvy pro <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody RW generuje kompilátor varování CC1036: &quot;Zjištěné volání metody 'System.String.IsNullOrWhteSpace(System.String)"bez [prázdná] v metodě.&quot; Toto je kompilátor varování spíše než chybu kompilátoru.|
|Doporučení|Toto chování se zákazníky a vyřešené v [339 # problém Githubu](https://github.com/Microsoft/CodeContracts/issues/339). Chcete-li odstranit toto upozornění, si můžete stáhnout a kompilaci aktualizovanou verzi zdrojového kódu pro nástroj kontrakty kódu z [Githubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Stáhněte si informace najdete v dolní části stránky.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

