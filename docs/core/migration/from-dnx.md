---
title: Migrace z DNX na .NET Core CLI
description: Migrujte z použití nástrojů DNX k .NET Core CLI nástrojů.
ms.date: 06/20/2016
ms.openlocfilehash: 31317f110ae1e8586b78becd757d0a8ff07f1459
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503830"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrace z DNX na .NET Core CLI (Project. JSON)

## <a name="overview"></a>Přehled
Verze RC1 rozhraní .NET Core a ASP.NET Core 1,0 představila nástroje DNX. Verze RC2 rozhraní .NET Core a ASP.NET Core 1,0 byla přesunuta z DNX do .NET Core CLI.

Jako mírnou aktualizační program si rekapitulace, co se DNX. DNX je modul runtime a sada nástrojů, která se používá k sestavování .NET Core a konkrétně k aplikacím ASP.NET Core 1,0. Skládá se ze 3 hlavních částí:

1. DNVM – instalační skript pro získání DNX
2. DNX (příkaz dotnet Execution Runtime) – modul runtime, který spouští váš kód
3. DNU (dotnet Developer Utility) – nástroje pro správu závislostí, vytváření a publikování aplikací

Při zavedení rozhraní příkazového řádku jsou nyní všechny výše uvedené součásti součástí jedné sady nástrojů. Vzhledem k tomu, že služba DNX byla k dispozici v časovém rámci RC1, možná máte vytvořené projekty, které chcete přesunout na nové nástroje rozhraní příkazového řádku.

Tato příručka k migraci se zabývá základy migrace projektů z DNX a na .NET Core CLI. Pokud právě začínáte projekt v .NET Core od začátku, můžete tento dokument volně přeskočit.

## <a name="main-changes-in-the-tooling"></a>Hlavní změny v nástrojích
Existují některé obecné změny v nástrojích, které by měly být nejprve popsaný.

### <a name="no-more-dnvm"></a>Žádné další DNVM
DNVM, short pro *dotnet Version Manager* , byl skript bash/PowerShellu, který se používá k instalaci DNX na vašem počítači. Pomohl uživatelům získat DNX, které potřebují z informačního kanálu, které zadal (nebo ve výchozím nastavení), a označit konkrétní DNX "aktivní", která by byla vložena do $PATH pro danou relaci. To vám umožní používat různé nástroje.

DNVM byla přerušena, protože její sada funkcí byla redundantní, protože změny přicházejí v .NET Core CLI.

CLI se vloží do balíčku dvěma hlavními způsoby:

1. Nativní instalační programy pro danou platformu
2. Nainstalovat skript pro jiné situace (například servery CI)

V takovém případě nejsou funkce instalace DNVM potřeba. Ale co o funkcích výběru za běhu?

V `project.json` odkazujete na modul runtime přidáním balíčku určité verze k vašim závislostem. V této změně bude vaše aplikace moci používat nové běhové bity. Načítání těchto bitů do počítače je stejné jako u rozhraní příkazového řádku: modul runtime nainstalujete pomocí jednoho z nativních instalačních programů, které podporuje nebo prostřednictvím instalačního skriptu.

### <a name="different-commands"></a>Různé příkazy
Pokud jste používali DNX, použili jste některé příkazy z jedné ze tří částí (DNX, DNU nebo DNVM). V rozhraní příkazového řádku se některé z těchto příkazů změní, některé nejsou k dispozici a některé jsou stejné, ale mají mírně odlišnou sémantiku.

Následující tabulka ukazuje mapování mezi příkazy DNX/DNU a jejich protějšky CLI.

| DNX – příkaz                    | CLI – příkaz    | Popis                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| DNX spuštění                        | `dotnet run`     | Spustí kód ze zdroje.                                                                                           |
| dnu sestavení                      | `dotnet build`   | Sestavte binární soubor IL vašeho kódu.                                                                                |
| dnu Pack                       | `dotnet pack`    | Zabalit balíček NuGet vašeho kódu.                                                                        |
| DNX \[příkaz] (například "DNX web") | Není k dispozici\*          | V DNX World spusťte příkaz definovaný v projektu Project. JSON.                                                     |
| instalace dnu                    | Není k dispozici\*          | V DNX World nainstalujte balíček jako závislost.                                                            |
| dnu obnovení                    | `dotnet restore` | Obnoví závislosti zadané v projektu. JSON. ([Viz poznámku](#dotnet-restore-note))                                                            |
| publikování dnu                    | `dotnet publish` | Publikujte aplikaci pro nasazení v jedné ze tří forem (přenosné, přenosné s nativní a samostatnou). |
| dnu zalomení                       | Není k dispozici\*          | V DNX World zabalte Project. JSON ve csproj.                                                                    |
| příkazy dnu                   | Není k dispozici\*          | V DNX World spravujte globálně nainstalované příkazy.                                                           |

(\*) – tyto funkce nejsou v rozhraní příkazového řádku v rámci návrhu podporovány.

## <a name="dnx-features-that-are-not-supported"></a>Nepodporované funkce DNX
Jak vidíte v tabulce výše, jsou k dispozici funkce z DNX světa, které jsme se rozhodli, že v rozhraní příkazového řádku nepodporujeme aspoň po dobu. Tato část prochází nejdůležitějšími a vysvětluje odůvodnění tím, že je nepodporují, a alternativní řešení, pokud je potřebujete.

### <a name="global-commands"></a>Globální příkazy
DNU byl dodán s konceptem s názvem "globální příkazy". V podstatě byly konzolové aplikace zabalené jako balíčky NuGet pomocí skriptu prostředí, který by vyvolal DNX, který jste zadali ke spuštění aplikace.

Rozhraní příkazového řádku nepodporuje tento koncept. Nicméně podporuje koncept přidávání příkazů pro projekt, které lze vyvolat pomocí známé `dotnet <command>` syntaxe.

### <a name="installing-dependencies"></a>Instalace závislostí
Od verze V1 nemá .NET Core CLI k dispozici `install` příkaz pro instalaci závislostí. Aby bylo možné nainstalovat balíček z nástroje NuGet, je nutné jej přidat jako závislost do souboru `project.json` a potom spustit `dotnet restore` ([Viz poznámku](#dotnet-restore-note)).

### <a name="running-your-code"></a>Spuštění kódu
Existují dva hlavní způsoby, jak kód spustit. Jedna je ze zdroje, s `dotnet run`. Na rozdíl od `dnx run`to neprovede žádnou kompilaci v paměti. Ve skutečnosti vyvolá `dotnet build` sestavení kódu a potom spustí sestavený binární soubor.

Dalším způsobem je použití samotného `dotnet` ke spuštění kódu. To se provádí zadáním cesty k sestavení: `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrace projektu DNX na .NET Core CLI
Kromě použití nových příkazů při práci s vaším kódem jsou v migraci z DNX tři hlavní věci:

1. Pokud máte přístup k rozhraní příkazového řádku, migrujte soubor `global.json`.
2. Migrace souboru projektu (`project.json`) sama na nástroje rozhraní příkazového řádku.
3. Migrace všech DNX rozhraní API na své BCL protějšky.

### <a name="changing-the-globaljson-file"></a>Změna souboru Global. JSON
Soubor `global.json` funguje jako soubor řešení pro projekty RC1 a RC2 (nebo novější). Aby se .NET Core CLI (stejně jako aplikace Visual Studio) rozlišila mezi RC1 a novějšími verzemi, používají vlastnost `"sdk": { "version" }` k tomu, aby byl rozlišený, který projekt je RC1 nebo novější. Pokud `global.json` nemá tento uzel vůbec, předpokládá se to jako poslední.

Chcete-li aktualizovat soubor `global.json`, buď odeberte vlastnost nebo ji nastavte na přesnou verzi nástrojů, které chcete použít, v tomto případě **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migruje se soubor projektu.

Rozhraní příkazového řádku a DNX používají stejný základní systém projektu na základě `project.json` souboru. Syntaxe a sémantika souboru projektu je poměrně velká a s malým rozdílem na základě scénářů. K dispozici jsou také některé změny schématu, které lze zobrazit v [souboru schématu](http://json.schemastore.org/project).

Pokud vytváříte konzolovou aplikaci, je nutné do souboru projektu přidat následující fragment kódu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Tímto dáte `dotnet build`, aby vygenerovala vstupní bod pro vaši aplikaci a efektivně tak spustitelný kód. Pokud vytváříte knihovnu tříd, jednoduše vynechejte výše uvedenou část. Samozřejmě, když přidáte výše uvedený fragment kódu do souboru `project.json`, je nutné přidat statický vstupní bod. Při přesunutí z DNX již není k dispozici služba DI Services, kterou poskytuje, proto musí být základním vstupním bodem .NET: `static void Main()`.

Pokud máte v `project.json`oddíl Commands, můžete ho odebrat. Některé příkazy, které se používají jako DNU příkazy, například Entity Framework příkazy rozhraní příkazového řádku, se předávají do rozhraní příkazového řádku jako rozšíření pro jednotlivé projekty. Pokud jste vytvořili vlastní příkazy, které používáte v projektech, je nutné je nahradit rozšířeními rozhraní příkazového řádku. V takovém případě musí být uzel `commands` v `project.json` nahrazen uzlem `tools` a musí obsahovat seznam závislostí nástrojů.

Po dokončení těchto akcí se musíte rozhodnout, jaký typ přenositelnosti chcete mít pro vaši aplikaci. S .NET Core jsme investovali do poskytování spektra možností přenositelnosti, ze kterých si můžete vybrat. Například může být vhodné mít plně *přenosné* aplikace nebo může chtít mít *samostatnou* aplikaci. Možnost přenosné aplikace je větší, jako .NET Framework aplikace funguje: potřebuje sdílenou komponentu, aby ji bylo možné spustit na cílovém počítači (.NET Core). Samostatně obsažená aplikace nevyžaduje instalaci .NET Core na cíl, ale musíte pro každý operační systém, který chcete podporovat, vydávat jednu aplikaci. Tyto typy přenositelnosti a další jsou popsány v dokumentu [typu přenositelnosti aplikace](../deploying/index.md) .

Jakmile zavoláte, jaký typ přenositelnosti chcete, musíte změnit cílové rozhraní. Pokud jste zapisovali aplikace pro .NET Core, pravděpodobně jste jako cílové rozhraní používali `dnxcore50`. V rozhraní příkazového řádku a změny, které nově [.NET Standard](../../standard/net-standard.md) , musí být rozhraní jedna z následujících:

1. `netcoreapp1.0` – Pokud píšete aplikace v .NET Core (včetně ASP.NET Corech aplikací)
2. `netstandard1.6` – Pokud píšete knihovny tříd pro .NET Core

Pokud používáte jiné cíle `dnx`, jako `dnx451`, budete je muset změnit také. `dnx451` by měl být změněn na `net451`.
Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md) .

Vaše `project.json` je teď většinou připravená. Musíte projít seznam závislostí a aktualizovat závislosti na jejich novějších verzích, zejména pokud používáte závislosti ASP.NET Core. Pokud jste používali samostatné balíčky pro rozhraní API BCL, můžete použít balíček modulu runtime, jak je vysvětleno v dokumentu [typ přenositelnosti aplikace](../deploying/index.md) .

Až budete připraveni, můžete se pokusit o obnovení pomocí `dotnet restore` ([Viz poznámku](#dotnet-restore-note)). V závislosti na verzi vašich závislostí může dojít k chybám, pokud NuGet nemůže vyřešit závislosti pro jednu z cílových rozhraní výše. Jedná se o problém "k určitému bodu v čase"; v průběhu času bude více a více balíčků zahrnovat podporu pro tyto architektury. Prozatím, pokud narazíte na to, můžete použít příkaz `imports` v rámci `framework` uzlu k určení balíčku NuGet, že může obnovit balíčky cílené na rozhraní v rámci příkazu Imports.
Chyby obnovení, které v tomto případě získáte, by měly poskytnout dostatek informací, abychom vám sdělili, které architektury potřebujete importovat. Pokud dojde ke mírné ztrátě nebo novému tomu, v obecném případě určení `dnxcore50` a `portable-net45+win8` v příkazu `imports` by měl být štych. Následující fragment kódu JSON ukazuje, jak vypadá takto:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Spuštění `dotnet build` zobrazí všechny chyby sestavení, i když by nemělo být příliš mnoho z nich. Poté, co kód sestaví a funguje správně, můžete ho otestovat pomocí spouštěče. Spusťte `dotnet <path-to-your-assembly>` a podívejte se na to.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
