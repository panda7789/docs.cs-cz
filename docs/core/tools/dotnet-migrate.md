---
title: DotNet migrate příkaz
description: Dotnet migrate příkaz migruje projektu a všechny jeho závislosti.
ms.date: 05/25/2018
ms.openlocfilehash: 73e0169e64be4b55e10127ecca0101885061767e
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170740"
---
# <a name="dotnet-migrate"></a>DotNet migrate

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet migrate` -Migruje projektu .NET Core 2 ve verzi Preview do projektu .NET Core SDK 1.0.

## <a name="synopsis"></a>Souhrn

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Popis

`dotnet migrate` Příkaz migraci platné ve verzi Preview 2 *project.json*– na základě projektu platný .NET Core SDK 1.0 *csproj* projektu.

Ve výchozím nastavení příkaz migruje kořenového projektu a všechny odkazy projektu, které obsahuje projekt kořenové. Toto chování je zakázáno použití `--skip-project-references` možnost za běhu.

Migrace lze provést na následující prostředky:

* Zadáním jednoho projektu *project.json* souboru migrace.
* Všechny adresáře určené v *global.json* předáním cesty k souboru *global.json* souboru.
* A *solution.sln* souboru, kde migruje projekty odkazované v řešení.
* Na všechny podadresáře rekurzivně zadaného adresáře.

`dotnet migrate` Příkaz udržuje migrovaných *project.json* soubor uvnitř `backup` adresáře, který vytvoří, pokud adresář neexistuje. Toto chování je přepsat pomocí `--skip-backup` možnost.

Ve výchozím nastavení vypíše operace migrace stavu procesu migrace do standardního výstupního (STDOUT). Pokud používáte `--report-file <REPORT_FILE>` možnost, výstup bude uložen do souboru zadejte.

`dotnet migrate` Platné ve verzi Preview 2 podporuje pouze příkaz *project.json*-projektů založených na. To znamená, že je nelze použít k migraci DNX nebo ve verzi Preview 1 *project.json*– na základě projekty přímo do projektů MSBuild/csproj. Nejdřív musíte ručně provést migraci projekt na verzi Preview 2 *project.json*– na základě projektu a pak `dotnet migrate` příkaz chcete projekt migrovat.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Cesta k jednomu z následujících akcí:

* *project.json* souboru migrace.
* *global.json* souboru: složky zadané v *global.json* se migrují.
* *solution.sln* souboru: projekty odkazované v řešení se migrují.
* adresář pro migraci: rekurzivně vyhledává *project.json* soubory určené k migraci do zadaného adresáře.

Výchozí hodnota je do aktuálního adresáře, pokud není zadáno žádné umístění.

## <a name="options"></a>Možnosti

`--format-report-file-json <REPORT_FILE>`

Výstup souboru sestavy migrace jako JSON a nikoli uživatele zprávy.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-r|--report-file <REPORT_FILE>`

Sestava migrace výstup do souboru kromě konzole.

`-s|--skip-project-references [Debug|Release]`

Přeskočit migrace projekt odkazuje. Ve výchozím nastavení odkazy na projekt jsou migrované rekurzivně.

`--skip-backup`

Přeskočit přesun *project.json*, *global.json*, a  *\*xproj* k `backup` adresáře po úspěšné migraci.

`-t|--template-file <TEMPLATE_FILE>`

Soubor csproj šablonu chcete použít pro migraci. Ve výchozím nastavení, stejné šablony jako zrušených správcem `dotnet new console` se používá.

`-v|--sdk-package-version <VERSION>`

Verze balíčku sady sdk, na který odkazuje migrované aplikace. Výchozí hodnota je verze sady SDK v `dotnet new`.

`-x|--xproj-file <FILE>`

Cesta k souboru xproj používat. Povinné, když je více než jeden xproj v adresáři projektu.

## <a name="examples"></a>Příklady

Migrate projekt v aktuálním adresáři a všechny jeho závislosti projektu na projekt:

`dotnet migrate`

Migrovat všechny projekty, které *global.json* soubor obsahuje:

`dotnet migrate path/to/global.json`

Migrujte pouze pro aktuální projekt a nemá žádné závislosti projektu na projekt (P2P). Také použijte konkrétní verzi sady SDK:

`dotnet migrate -s -v 1.0.0-preview4`