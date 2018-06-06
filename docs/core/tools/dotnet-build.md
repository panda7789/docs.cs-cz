---
title: DotNet sestavení command - .NET Core rozhraní příkazového řádku
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislé součásti.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 6b0b7bc11b560d8632b38f1dfa4e7eb3ce6c54d2
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697128"
---
# <a name="dotnet-build"></a>sestavení pro DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet build` -Sestavení projektu a všechny jeho závislé součásti.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet build` Příkaz sestavení projektu a jeho závislosti do sady binárních souborů. Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění pomocí *PDB* rozšíření. Soubor JSON závislosti (*\*. deps.json*) vytváří, jsou uvedené závislosti aplikace. A  *\*. runtimeconfig.json* vytvořil soubor, který určuje sdílený modul runtime a její verzi pro aplikaci.

Pokud projekt má závislosti třetích stran, například knihoven z NuGet, se z mezipaměti NuGet rozpoznána a nejsou k dispozici integrované výstup projektu. Si uvědomit, produkt `dotnet build` není připraven k přesunu do jiného počítače ke spuštění. Tím se liší od chování rozhraní .NET Framework v které vytváření spustitelný projekt (aplikace) vytváří výstup, který je spustitelného na libovolném počítači nainstalovanou rozhraní .NET Framework. Pokud chcete, aby na podobném principu s .NET Core, budete muset použít [dotnet publikování](dotnet-publish.md) příkaz. Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Vytváření vyžaduje *project.assets.json* souboru, který uvádí závislosti vaší aplikace. Soubor je vytvořen, když [ `dotnet restore` ](dotnet-restore.md) se spustí. Bez souboru prostředků v místě nelze nástroji vyřešit referenční sestavení, což vede k chybám. S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`. Od verze rozhraní .NET Core SDK 2.0, `dotnet restore` implicitně spouští při spuštění `dotnet build`. Pokud chcete zakázat implicitní obnovení při spuštění příkazu sestavení, můžete předat `--no-restore` možnost.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

`dotnet build` používá pro sestavení projektu MSBuild, takže podporuje paralelní i přírůstkové sestavení. Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).

Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `/p` pro nastavení vlastností nebo `/l` k definování protokolovacího nástroje. Další informace o těchto možnostech najdete v tématu [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

Jestli je projekt spustitelný soubor nebo ne je dáno `<OutputType>` vlastnost v souboru projektu. Následující příklad ukazuje projekt, který vytváří spustitelného kódu:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Chcete-li vytvořit knihovnu, vynechejte `<OutputType>` vlastnost. Hlavní rozdíl ve vytvořené výstupu je, že IL DLL pro knihovnu neobsahuje vstupní body a nelze provést.

## <a name="arguments"></a>Arguments

`PROJECT`

K vytvoření souboru projektu. Pokud projekt soubor není zadán, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, které *proj* a použije tento soubor.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Zkompiluje pro konkrétní [framework](../../standard/frameworks.md). Rozhraní musí být definován v [soubor projektu](csproj.md).

`--force`

Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--no-dependencies`

Ignoruje odkazů (P2P) projekt na projekt a pouze sestavení projektu zadaný kořenový.

`--no-incremental`

Označí sestavení jako bezpečné pro přírůstkové sestavení. Tento příznak vypne přírůstkové kompilace a vynutí čistou opětovné sestavení grafu závislostí projektu.

`--no-restore`

Neprovede implicitní obnovení během vytváření sestavení.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, do níž umístíte integrovaný binární soubory. Budete také muset definovat `--framework` Pokud zadáte tuto možnost.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje verze přípona hvězdičku (`*`) v poli verze souboru projektu. Formát řídí pokyny verze NuGet.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Zkompiluje pro konkrétní [framework](../../standard/frameworks.md). Rozhraní musí být definován v [soubor projektu](csproj.md).

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--no-dependencies`

Ignoruje odkazů (P2P) projekt na projekt a pouze sestavení projektu zadaný kořenový.

`--no-incremental`

Označí sestavení jako bezpečné pro přírůstkové sestavení. Tento příznak vypne přírůstkové kompilace a vynutí čistou opětovné sestavení grafu závislostí projektu.

`-o|--output <OUTPUT_DIRECTORY>`

Adresář, do níž umístíte integrovaný binární soubory. Budete také muset definovat `--framework` Pokud zadáte tuto možnost.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje verze přípona hvězdičku (`*`) v poli verze souboru projektu. Formát řídí pokyny verze NuGet.

---

## <a name="examples"></a>Příklady

Sestavte projekt a jeho závislé součásti:

`dotnet build`

Sestavte projekt a jeho závislosti pomocí konfigurace verze:

`dotnet build --configuration Release`

Sestavte projekt a jeho závislosti pro konkrétní runtime (v tomto příkladu Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`

Sestavte projekt a použijte zadaný zdroj balíčku NuGet během operace obnovení (.NET Core SDK 2.0 a novější):

`dotnet build --source c:\packages\mypackages`