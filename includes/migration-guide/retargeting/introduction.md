## <a name="introduction"></a>Úvod
Změna orientace změny ovlivňují aplikace, které jsou překompilovat cílit na různých rozhraní .NET Framework. Mezi ně patří:

* Změny prostředí v době návrhu. Například nástroje sestavení mohou vygenerovat upozornění, které před tím negenerovaly.

* Změny v prostředí modulu runtime. Tato ovlivňují jenom aplikace, která se specificky zaměřují přesměrovanou rozhraní .NET Framework. Aplikace, které cílí na předchozí verze rozhraní .NET Framework, se chovají stejným způsobem, jako by byly spuštěny v těchto verzích.

V tématech, které popisují Změna orientace změny budeme mít klasifikované jednotlivé položky podle jejich očekávaného dopadu, následujícím způsobem:

**Hlavní** jde významné změny, které ovlivní velký počet aplikací, nebo který vyžaduje významné úpravu kódu.

**Méně závažné** jedná se o změnu, která ovlivňuje malý počet aplikací nebo který vyžaduje menší úpravu kódu.

**Okraj případ** jedná se o změnu, která má vliv na aplikace v rámci velmi konkrétní scénáře, které nejsou běžné.

**Transparentní** jedná se o změnu, která nemá žádný znatelný vliv na vývojáře aplikace nebo uživatele. Z důvodu této změny by aplikace neměla vyžadovat úpravy.
