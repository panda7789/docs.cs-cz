---
title: "příkaz - .NET Core rozhraní příkazového řádku migrovat DotNet."
description: "Migrace dotnet příkaz migruje projektu a všechny jeho závislé součásti."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 7fad6bf67dfe7b0d6f70ce527a153080aa17d888
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-migrate"></a>migrace DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet migrate`-Migruje Preview 2 .NET Core projektu na .NET Core SDK 1.0 projekt.

## <a name="synopsis"></a>Stručný obsah

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a>Popis

`dotnet migrate` Příkaz migruje platný Preview 2 *project.json*– na základě projekt, který má platný .NET Core SDK 1.0 *csproj* projektu. 

Ve výchozím nastavení příkaz migruje kořenového projektu a všechny odkazy na projekt, které kořenové projekt obsahuje. Toto chování je zakázat pomocí `--skip-project-references` možnost za běhu. 

Migrace se provádí na následující:

* Jeden projekt tak, že zadáte *project.json* souboru migrace.
* Všechny adresáře zadaný v *global.json* předáním cesty k souboru *global.json* souboru.
* A *solution.sln* souboru, kde se migruje projekty v řešení odkazuje.
* Na všechny podadresáře rekurzivně zadaného adresáře.

`dotnet migrate` Příkaz udržuje migrovaných *project.json* souboru uvnitř `backup` adresáři, který vytvoří, pokud adresář neexistuje. Toto chování je přepsat pomocí `--skip-backup` možnost.

Ve výchozím nastavení výstupy operace migrace stavu procesu migrace do standardního výstupního (STDOUT). Pokud použijete `--report-file <REPORT_FILE>` možnost výstup bude uložen do souboru zadejte. 

`dotnet migrate` Platný Preview 2 podporuje pouze příkaz *project.json*– projekty založené na. To znamená, že je nemůžete použít k migraci DNX nebo Preview 1 *project.json*– projekty přímo do projektů MSBuild/csproj založené na. Je nutné nejprve ručně migrovat projekt do Preview 2 *project.json*– na základě projektu a pak použít `dotnet migrate` k migraci projektu.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Cesta k jednomu z následujících akcí:

* *project.json* souboru migrace.
* *global.json* souboru se bude migrovat složky specifikované v *global.json*.
* *solution.sln* souboru se bude migrovat projekty v řešení odkazuje.
* adresář, který chcete migrovat, ji budou rekurzivní hledání *project.json* soubory určené k migraci.

Výchozí hodnota je aktuální adresář, pokud není zadáno žádné umístění.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-t|--template-file <TEMPLATE_FILE>`

Soubor csproj šablonu použít pro migraci. Ve výchozím nastavení, stejné šablony jako ten, zrušených `dotnet new console` se používá.

`-v|--sdk-package-version <VERSION>`

Verze balíčku sdk, který se odkazuje v migrovanou aplikaci. Výchozí hodnota je verze sady SDK v `dotnet new`.

`-x|--xproj-file <FILE>`

Cesta k souboru xproj používat. Vyžaduje, když je více než jeden xproj v adresáři projektu.

`-s|--skip-project-references [Debug|Release]`

Přeskočit migrace projekt odkazuje. Ve výchozím nastavení jsou odkazy na projekt migrované rekurzivně.

`-r|--report-file <REPORT_FILE>`

Sestavy migrace výstup do souboru kromě konzole.

`--format-report-file-json <REPORT_FILE>`

Soubor sestavy migrace výstup jako JSON, místo uživatelských zprávy.

`--skip-backup`

Přeskočit přesunutí *project.json*, *global.json*, a  *\*.xproj* k `backup` adresář po úspěšné migraci.

## <a name="examples"></a>Příklady

Migrace na projekt v aktuálním adresáři a všechny jeho závislosti projektu projektu:

`dotnet migrate`

Migrovat všechny projekty, které *global.json* soubor obsahuje:

`dotnet migrate path/to/global.json`

Migrujte pouze aktuální projekt a nemá žádné závislosti projektu k projektu (P2P). Také použijte konkrétní verzi sady SDK:

`dotnet migrate -s -v 1.0.0-preview4`
