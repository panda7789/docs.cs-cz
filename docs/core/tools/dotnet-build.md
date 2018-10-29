---
title: DotNet sestavení příkaz – rozhraní příkazového řádku .NET Core
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislosti.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: c9d1478e3d3e298b01e707242cc7ad5cd924a9b3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200547"
---
# <a name="dotnet-build"></a>DotNet sestavení

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet build` -Sestavení projektu a všechny jeho závislosti.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet build` Příkaz sestaví projekt a jeho závislosti do sady binární soubory. Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění v sadě *PDB* rozšíření. Soubor JSON závislosti (*\*. deps.json*) je vytvořen, který obsahuje seznam závislostí aplikace. A  *\*. runtimeconfig.json* je vytvořen soubor, který určuje sdílený modul runtime a jeho verze pro aplikaci.

Obsahuje-li projekt závislostí třetích stran, jako jsou knihovny z Nugetu, že vyřešit z mezipaměti NuGet a nejsou k dispozici s sestavení výstupu projektu. Skutečností, součin `dotnet build` není připravené k převedení do jiného počítače ke spuštění. To se liší od chování rozhraní .NET Framework ve které vytváření spustitelného souboru projektu (aplikace) vytvoří výstup, který je spustitelný na libovolný počítač, ve kterém je nainstalováno rozhraní .NET Framework. Pokud chcete, aby fungují na podobném principu s .NET Core, budete muset použít [dotnet publikovat](dotnet-publish.md) příkazu. Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Vytváření vyžaduje *project.assets.json* soubor, který obsahuje seznam závislostí vaší aplikace. Soubor je vytvořen při [ `dotnet restore` ](dotnet-restore.md) provádí. Bez souboru prostředků v místě nelze nástrojů vyřešit referenční sestavení, což má za následek chyby. S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`. Počínaje .NET Core 2.0 SDK `dotnet restore` se implicitně spouští při spuštění `dotnet build`. Pokud chcete zakázat implicitní obnovení při spuštění příkazu k sestavení, lze předat `--no-restore` možnost.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

`dotnet build` používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení. Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).

Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `-p` pro nastavení vlastnosti nebo `-l` k definování protokolovač. Další informace o těchto možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference).

Určuje, zda je projekt spustitelné nebo ne je určeno `<OutputType>` vlastnost v souboru projektu. Následující příklad ukazuje projekt, který vytvoří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Pokud chcete vytvořit knihovnu, vynechejte `<OutputType>` vlastnost. Hlavní rozdíl v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ho provést.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Soubor projektu nebo řešení pro sestavení. Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *proj* nebo *sln* a použije tento soubor.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Zkompiluje pro konkrétní [framework](../../standard/frameworks.md). Rozhraní musí být definován v [soubor projektu](csproj.md).

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--no-dependencies`

Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).

`--no-incremental`

Označí sestavení jako problematické pro přírůstkové sestavení. Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.

`--no-restore`

Neprovede implicitní obnovení během sestavování.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, do kterého chcete sestavené binární soubory. Budete také muset definovat `--framework` při zadání této možnosti.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu. Formát řídí pokyny verze Nugetu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Zkompiluje pro konkrétní [framework](../../standard/frameworks.md). Rozhraní musí být definován v [soubor projektu](csproj.md).

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--no-dependencies`

Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).

`--no-incremental`

Označí sestavení jako problematické pro přírůstkové sestavení. Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, do kterého chcete sestavené binární soubory. Budete také muset definovat `--framework` při zadání této možnosti.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje, verze přípona hvězdičku (`*`) v poli verze souboru projektu. Formát řídí pokyny verze Nugetu.

---

## <a name="examples"></a>Příklady

Sestavení projektu a jeho závislosti:

`dotnet build`

Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:

`dotnet build --configuration Release`

Sestavení projektu a jeho závislosti pro konkrétní prostředí runtime (v tomto příkladu se systémem Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`

Sestavte projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core SDK 2.0 a novější):

`dotnet build --source c:\packages\mypackages`