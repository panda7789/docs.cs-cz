---
title: dotnet migrate, příkaz
description: Příkaz migrace dotnet migruje projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 6148048c469c43320cc4459352fd2fb62f101740
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503694"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Tento článek se týká:** ✔️ .NET Core 2.x SDK

## <a name="name"></a>Name (Název)

`dotnet migrate`- Migruje projekt Preview 2 .NET Core do projektu ve stylu sady .NET Core SDK.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Popis

Tento příkaz je zastaralé. Příkaz `dotnet migrate` již není k dispozici počínaje sadou .NET Core 3.0 SDK. Může migrovat pouze projekt Preview 2 .NET Core do projektu 1.x .NET Core, který je mimo podporu.

Ve výchozím nastavení příkaz migruje kořenový projekt a všechny odkazy na projekt, které kořenový projekt obsahuje. Toto chování je `--skip-project-references` zakázáno pomocí možnosti za běhu.

Migraci lze provést u následujících prostředků:

* Jeden projekt zadáním souboru *project.json* k migraci.
* Všechny adresáře zadané v souboru *global.json* předáním v cestě k souboru *global.json.*
* Soubor *solution.sln,* kde migruje projekty odkazované v řešení.
* Ve všech podadresářích daného adresáře rekurzivně.

Příkaz `dotnet migrate` uchovává migrovaný soubor *project.json* uvnitř `backup` adresáře, který vytvoří, pokud adresář neexistuje. Toto chování je `--skip-backup` přepsáno pomocí možnosti.

Ve výchozím nastavení operace migrace vypisuje stav procesu migrace na standardní výstup (STDOUT). Pokud použijete `--report-file <REPORT_FILE>` tuto možnost, výstup se uloží do určeného souboru.

Příkaz `dotnet migrate` podporuje pouze platné projekty založené na *projektu.json*preview 2. To znamená, že jej nelze použít k migraci projektů založených na *projektu*DNX nebo Preview 1 přímo do projektů MSBuild/csproj. Nejprve je třeba ručně migrovat projekt do projektu.json verze `dotnet migrate` Preview 2 a potom pomocí příkazu k migraci projektu. *project.json*

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Cesta k jedné z následujících možností:

* soubor *u množení.*
* *global.json* soubor: složky zadané v *global.json* jsou migrovány.
* soubor *solution.sln:* projekty odkazované v řešení jsou migrovány.
* adresář pro migraci: rekurzivně vyhledá soubory *project.json,* které mají být migrovány uvnitř zadaného adresáře.

Pokud není nic zadáno, výchozí je aktuální adresář.

## <a name="options"></a>Možnosti

`--format-report-file-json <REPORT_FILE>`

Výstupní migrace soubor sestavy jako JSON spíše než uživatelské zprávy.

`-h|--help`

Vytiskne krátkou nápovědu pro příkaz.

`-r|--report-file <REPORT_FILE>`

Výstupní zpráva o migraci do souboru kromě konzoly.

`-s|--skip-project-references [Debug|Release]`

Přeskočení migrace odkazů na projekt Ve výchozím nastavení jsou odkazy na projekt migrovány rekurzivně.

`--skip-backup`

Po úspěšné migraci přeskočte `backup` přesunutí *souboru project.json*, *global.json*a * \*.xproj* do adresáře.

`-t|--template-file <TEMPLATE_FILE>`

Šablona csproj soubor pro migraci. Ve výchozím nastavení se používá stejná šablona, kterou jste upustili. `dotnet new console`

`-v|--sdk-package-version <VERSION>`

Verze balíčku sady SDK, na kterou odkazuje migrovaná aplikace. Výchozí je verze sady SDK `dotnet new`v .

`-x|--xproj-file <FILE>`

Cesta k souboru xproj, který chcete použít. Povinné v případě, že je více než jeden xproj v adresáři projektu.

## <a name="examples"></a>Příklady

Migrujte projekt v aktuálním adresáři a všechny jeho závislosti mezi projekty:

`dotnet migrate`

Migrace všech projektů, které soubor *global.json* obsahuje:

`dotnet migrate path/to/global.json`

Migrujte pouze aktuální projekt a žádné závislosti projektu k projektu (P2P). Použijte také konkrétní verzi sady SDK:

`dotnet migrate -s -v 1.0.0-preview4`
