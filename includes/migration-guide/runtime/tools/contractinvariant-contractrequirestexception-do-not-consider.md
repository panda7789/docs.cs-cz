### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant nebo Contract.Requires<TException> nepovažujte String.IsNullOrEmpty jako prázdnou

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí na rozhraní .NET Framework 4.6.1, pokud neutrální smlouvy pro <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> nebo kontrakt předběžnou <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> volání <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody RW vysílá kompilátoru upozornění CC1036: &quot;zjistil volání metody. System.String.IsNullOrWhteSpace(System.String)' bez [prázdná] v metodě.&quot; Toto je kompilátor upozornění místo chybě kompilátoru.|
|Návrh|Toto chování se řešeny v [339 # problém Githubu](https://github.com/Microsoft/CodeContracts/issues/339). Pokud chcete odstranit toto upozornění, si můžete stáhnout a kompilace zdrojového kódu pro nástroj kontrakty kódu z aktualizovaná verze [Githubu](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Stáhnout informace naleznete v dolní části stránky.|
|Rozsah|Vedlejší|
|Version|4.6.1|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

