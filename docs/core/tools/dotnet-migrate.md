---
title: dotnet – příkaz migrace
description: Příkaz dotnet migruje migruje projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 2e7f9ae5a1d11c54280d914b04df761f0d5aff99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284089"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Tento článek se týká:** ✔️ .NET Core 2. x SDK

## <a name="name"></a>Name

`dotnet migrate`– Migruje projekt .NET Core ve verzi Preview 2 na projekt ve stylu .NET Core SDK.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a>Popis

Tento příkaz je zastaralý. `dotnet migrate`Příkaz již není od sady .NET Core 3,0 SDK k dispozici. Může migrovat pouze projekt verze Preview 2 .NET Core do projektu .NET Core s 1. x, který není podporován.

Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy projektu, které obsahuje kořenový projekt. Toto chování je zakázáno pomocí `--skip-project-references` Možnosti v době běhu.

Migraci můžete provádět na těchto prostředcích:

* Jeden projekt zadáním souboru *Project. JSON* , který se má migrovat.
* Všechny adresáře zadané v souboru *Global. JSON* předáním cesty k souboru *Global. JSON* .
* Soubor *řešení. sln* , kde migruje projekty, na které je odkazováno v řešení.
* Ve všech podadresářích daného adresáře rekurzivně.

`dotnet migrate`Příkaz udržuje migrovaný soubor *Project. JSON* v `backup` adresáři, který vytvoří, pokud adresář neexistuje. Toto chování je přepsáno pomocí `--skip-backup` Možnosti.

Ve výchozím nastavení operace migrace vypíše stav procesu migrace do standardního výstupu (STDOUT). Použijete-li `--report-file <REPORT_FILE>` možnost, bude výstup uložen do souboru.

`dotnet migrate`Příkaz podporuje pouze platná verze Preview 2 projekty založené na *projektu. JSON*. To znamená, že ho nemůžete použít k migraci DNX nebo Preview 1 projektů založených na *Project. JSON*přímo do projektů MSBuild/csproj. Nejprve je třeba ručně migrovat projekt do projektu verze Preview 2 *Project. JSON*a potom použít `dotnet migrate` příkaz k migraci projektu.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Cesta k jednomu z následujících:

* soubor *Project. JSON* , který se má migrovat
* soubor *Global. JSON* : složky zadané v souboru *Global. JSON* se migrují.
* soubor *řešení. sln* : projekty odkazované v řešení jsou migrovány.
* Adresář, který se má migrovat: rekurzivně vyhledává soubory *Project. JSON* , které se mají migrovat do zadaného adresáře.

Použije se výchozí nastavení aktuální adresář, pokud není nic zadané.

## <a name="options"></a>Možnosti

`--format-report-file-json <REPORT_FILE>`

Výstupní soubor sestavy migrace jako JSON, nikoli zprávy uživatele

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`-r|--report-file <REPORT_FILE>`

Výstup sestavy migrace do souboru spolu s konzolou.

`-s|--skip-project-references [Debug|Release]`

Přeskočit migraci odkazů na projekt Ve výchozím nastavení jsou odkazy na projekt migrovány rekurzivně.

`--skip-backup`

Po úspěšné migraci můžete přeskočit přesunutí *Project. JSON*, *Global. JSON*a * \* . xproj* do `backup` adresáře.

`-t|--template-file <TEMPLATE_FILE>`

Soubor CSPROJ šablony, který se má použít pro migraci Ve výchozím nastavení se používá stejná šablona jako vyhozená `dotnet new console` .

`-v|--sdk-package-version <VERSION>`

Verze balíčku sady SDK, na který se odkazuje migrovaná aplikace Výchozím nastavením je verze sady SDK v nástroji `dotnet new` .

`-x|--xproj-file <FILE>`

Cesta k souboru xproj, který se má použít Požadováno v případě, že je v adresáři projektu více než jeden xproj.

## <a name="examples"></a>Příklady

Migrovat projekt v aktuálním adresáři a všech jeho závislostech mezi projekty:

`dotnet migrate`

Migrujte všechny projekty, které obsahuje soubor *Global. JSON* :

`dotnet migrate path/to/global.json`

Migrujte pouze aktuální projekt a žádné závislosti mezi projekty (P2P). Použijte také konkrétní verzi sady SDK:

`dotnet migrate -s -v 1.0.0-preview4`
