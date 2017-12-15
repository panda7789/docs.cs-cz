---
title: "příkaz pack DotNet - .NET Core rozhraní příkazového řádku"
description: "Příkaz pack dotnet vytvoří balíčky NuGet pro projekt .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 12/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: ac1ff90cb97fa4802883e70b0abdf4e77b58dd65
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="dotnet-pack"></a>pack DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet pack`-Pack kód do balíčku NuGet.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet pack` Příkaz vytvoří projekt a vytvořit balíčky NuGet. Výsledek tohoto příkazu je balíček NuGet. Pokud `--include-symbols` možnost nachází, je vytvořen jiný balíček obsahující symboly ladění.

Závislosti NuGet sbalené projektu se přidají do *příponou .nuspec* souboru tak, aby správně přeložit, když je balíček nainstalován. Odkazy na projekt na projekt nejsou zabalené do projektu. V současné době musí mít balíček podle projektů, pokud máte závislosti projektu k projektu.

Ve výchozím nastavení `dotnet pack` nejprve sestavení projektu. Pokud chcete-li se tomu vyhnout, předat `--no-build` možnost. Toto je často užitečný ve scénářích sestavení nepřetržité integrace (CI), které víte, že kód byl dříve vytvořený.

Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkazu pro proces okolních. Další informace najdete v tématu [NuGet metadata vlastnosti](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). [Příklady](#examples) část ukazuje způsob použití nástroje MSBuild přepínače pro několik různých scénářů.

## <a name="arguments"></a>Arguments

`PROJECT`

Projekt pack. Je buď cestu k [csproj souboru](csproj.md) nebo do adresáře. Při vynechání je použita k aktuálnímu adresáři.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`--force`Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Jde o ekvivalent odstraňování *project.assets.json* souboru.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--include-source`

Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.

`--include-symbols`

Generuje symboly `nupkg`.

`--no-build`

Není sestavení projektu před okolních.

`--no-dependencies`

Ignoruje odkazy na projekt na projekt a obnoví pouze kořenové projektu.

`--no-restore`

Neprovede implicitní obnovení, při spuštění příkazu.

`-o|--output <OUTPUT_DIRECTORY>`

Zadaný adresář umístí připravené balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

`-s|--serviceable`

Nastaví příznak obsluhovatelná v balíčku. Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--include-source`

Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.

`--include-symbols`

Generuje symboly `nupkg`.

`--no-build`

Není sestavení projektu před okolních.

`-o|--output <OUTPUT_DIRECTORY>`

Zadaný adresář umístí připravené balíčky.

`-s|--serviceable`

Nastaví příznak obsluhovatelná v balíčku. Další informace najdete v tématu [blogu .NET: technologie .NET 4.5.1 podporuje Microsoft Security aktualizací pro knihovny .NET NuGet](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Definuje hodnotu pro `$(VersionSuffix)` vlastnosti MSBuild v projektu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

---

## <a name="examples"></a>Příklady

Sada pro projekt v aktuálním adresáři:

`dotnet pack`

Sada `app1` projektu:

`dotnet pack ~/projects/app1/project.csproj`
    
Pack projekt v aktuálním adresáři a umístí do výsledného balíčky `nupkgs` složky:

`dotnet pack --output nupkgs`

Pack projekt v aktuálním adresáři do `nupkgs` složku a přeskočit krok sestavení:

`dotnet pack --no-build --output nupkgs`

V projektu je verze přípona nakonfigurovat jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souboru, pack aktuální projekt a aktualizaci výsledné verzi balíčku s příponou dané:

`dotnet pack --version-suffix "ci-1234"`

Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnosti MSBuild:

`dotnet pack /p:PackageVersion=2.1.0`

Pack projekt pro konkrétní [cílové rozhraní](../../standard/frameworks.md):

`dotnet pack /p:TargetFrameworks=net45`
