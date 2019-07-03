---
title: DotNet migrate příkaz
description: Dotnet migrate příkaz migruje projektu a všechny jeho závislosti.
ms.date: 06/26/2019
ms.openlocfilehash: 3304f666d15d9188cdae76a401747d91791f817f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539388"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet migrate` -Migruje do projektu .NET Core SDK – vizuální styl projektu .NET Core 2 ve verzi Preview.

> [!NOTE]
> `dotnet migrate` Odebere ze sady SDK .NET Core 3.0 v další vydané verzi preview.

## <a name="synopsis"></a>Souhrn

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Popis

`dotnet migrate` Příkaz migraci platné ve verzi Preview 2 *project.json*– na základě projektu platný sady SDK .NET Core – styl *csproj* projektu.

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
