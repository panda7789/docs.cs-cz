## <a name="introduction"></a>Úvod
Změny cíle ovlivňují aplikace, které jsou rekompilovány pro cílení různých rozhraní .NET Framework. Mezi ně patří:

* Změny prostředí v době návrhu. Například nástroje sestavení mohou vygenerovat upozornění, které před tím negenerovaly.

* Změny v prostředí modulu runtime. Tyto změny ovlivní pouze aplikace, které specificky cílí přesměrovanou rozhraní .NET Framework. Aplikace, které cílí na předchozí verze rozhraní .NET Framework, se chovají stejným způsobem, jako by byly spuštěny v těchto verzích.

V tématech, které popisují změny cíle, jsme jednotlivé položky klasifikovali podle jejich očekávaného dopadu, následujícím způsobem:

**Hlavní** jedná se o významnou změnu, která ovlivňuje mnoho aplikací nebo která vyžaduje podstatné změny kódu.

**Vedlejší** jedná se o změnu, která ovlivňuje menší počet aplikací nebo která vyžaduje méně závažnou změnu kódu.

**Okraj případ** jedná se o změnu, která ovlivňuje aplikace v konkrétních situacích, jež nejsou běžné.

**Transparentní** jedná se o změnu, která nemá znatelný vliv na uživatele nebo vývojáře aplikace. Z důvodu této změny by aplikace neměla vyžadovat úpravy.
