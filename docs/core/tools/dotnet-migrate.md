---
title: dotnet – příkaz migrace
description: Příkaz dotnet migruje migruje projekt a všechny jeho závislosti.
ms.date: 06/26/2019
ms.openlocfilehash: 86f11592e774da12b010886aaa1e30cee063fea6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202532"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet migrate`– Migruje projekt .NET Core ve verzi Preview 2 na projekt ve stylu .NET Core SDK.

> [!NOTE]
> `dotnet migrate`v příští verzi Preview se odebere ze sady .NET Core 3,0 SDK.

## <a name="synopsis"></a>Stručný obsah

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Popis

Příkaz migruje platný projekt založený na verzi Preview 2 *Project. JSON*na platný projekt csproj ve stylu .NET Core SDK. `dotnet migrate`

Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy projektu, které obsahuje kořenový projekt. Toto chování je zakázáno pomocí `--skip-project-references` možnosti za běhu.

Migraci můžete provádět na těchto prostředcích:

* Jeden projekt zadáním souboru *Project. JSON* , který se má migrovat.
* Všechny adresáře zadané v souboru *Global. JSON* předáním cesty k souboru *Global. JSON* .
* Soubor *řešení. sln* , kde migruje projekty, na které je odkazováno v řešení.
* Ve všech podadresářích daného adresáře rekurzivně.

Příkaz udržuje migrovaný soubor *Project. JSON* v `backup` adresáři, který vytvoří, pokud adresář neexistuje. `dotnet migrate` Toto chování je přepsáno `--skip-backup` pomocí možnosti.

Ve výchozím nastavení operace migrace vypíše stav procesu migrace do standardního výstupu (STDOUT). Použijete-li `--report-file <REPORT_FILE>` možnost, bude výstup uložen do souboru.

Příkaz podporuje pouze platná verze Preview 2 projekty založené na *projektu. JSON.* `dotnet migrate` To znamená, že ho nemůžete použít k migraci DNX nebo Preview 1 projektů založených na *Project. JSON*přímo do projektů MSBuild/csproj. Nejprve je třeba ručně migrovat projekt do projektu verze Preview 2 *Project. JSON*a potom použít `dotnet migrate` příkaz k migraci projektu.

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

Po úspěšné migraci můžete přeskočit přesunutí *Project. JSON*, *Global. JSON*a  *\*. xproj* do `backup` adresáře.

`-t|--template-file <TEMPLATE_FILE>`

Soubor CSPROJ šablony, který se má použít pro migraci Ve výchozím nastavení `dotnet new console` se používá stejná šablona jako vyhozená.

`-v|--sdk-package-version <VERSION>`

Verze balíčku sady SDK, na který se odkazuje migrovaná aplikace Výchozím nastavením je verze sady SDK v `dotnet new`nástroji.

`-x|--xproj-file <FILE>`

Cesta k souboru xproj, který se má použít Požadováno v případě, že je v adresáři projektu více než jeden xproj.

## <a name="examples"></a>Příklady

Migrovat projekt v aktuálním adresáři a všech jeho závislostech mezi projekty:

`dotnet migrate`

Migrujte všechny projekty, které obsahuje soubor *Global. JSON* :

`dotnet migrate path/to/global.json`

Migrujte pouze aktuální projekt a žádné závislosti mezi projekty (P2P). Použijte také konkrétní verzi sady SDK:

`dotnet migrate -s -v 1.0.0-preview4`
