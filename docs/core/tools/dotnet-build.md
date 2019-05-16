---
title: příkaz DotNet sestavení
description: Dotnet sestavení příkaz sestavení projektu a všechny jeho závislosti.
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632138"
---
# <a name="dotnet-build"></a>DotNet sestavení

**Tento článek se týká: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet build` -Sestavení projektu a všechny jeho závislosti.

## <a name="synopsis"></a>Souhrn

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Popis

`dotnet build` Příkaz sestaví projekt a jeho závislosti do sady binární soubory. Binární soubory zahrnují projektu kódu v souborech Intermediate Language (IL) s *.dll* rozšíření a symbol soubory používané pro ladění v sadě *PDB* rozšíření. Soubor JSON závislosti (*\*. deps.json*) je vytvořen, který obsahuje seznam závislostí aplikace. A  *\*. runtimeconfig.json* je vytvořen soubor, který určuje sdílený modul runtime a jeho verze pro aplikaci.

Obsahuje-li projekt závislostí třetích stran, jako jsou knihovny z Nugetu, že vyřešit z mezipaměti NuGet a nejsou k dispozici s sestavení výstupu projektu. Skutečností, součin `dotnet build` není připravené k převedení do jiného počítače ke spuštění. To se liší od chování rozhraní .NET Framework ve které vytváření spustitelného souboru projektu (aplikace) vytvoří výstup, který je spustitelný na libovolný počítač, ve kterém je nainstalováno rozhraní .NET Framework. Pokud chcete, aby fungují na podobném principu s .NET Core, budete muset použít [dotnet publikovat](dotnet-publish.md) příkazu. Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Vytváření vyžaduje *project.assets.json* soubor, který obsahuje seznam závislostí vaší aplikace. Soubor je vytvořen při [ `dotnet restore` ](dotnet-restore.md) provádí. Bez souboru prostředků v místě nelze nástrojů vyřešit referenční sestavení, což má za následek chyby. S .NET Core 1.x SDK potřebné ke spuštění explicitně `dotnet restore` dřív, než spustíte `dotnet build`. Počínaje .NET Core 2.0 SDK `dotnet restore` se implicitně spouští při spuštění `dotnet build`. Pokud chcete zakázat implicitní obnovení při spuštění příkazu k sestavení, lze předat `--no-restore` možnost.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Určuje, zda je projekt spustitelné nebo ne je určeno `<OutputType>` vlastnost v souboru projektu. Následující příklad ukazuje projekt, který vytvoří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

K vytvoření knihovny vynechat, nechte `<OutputType>` vlastnost. Hlavní rozdíl v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ho provést.

### <a name="msbuild"></a>MSBuild

`dotnet build` používá MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení. Další informace najdete v tématu [přírůstková sestavení](/visualstudio/msbuild/incremental-builds).

Kromě jeho možností `dotnet build` příkaz přijímá MSBuild možnosti, jako například `-p` pro nastavení vlastnosti nebo `-l` k definování protokolovač. Další informace o těchto možnostech najdete v tématu [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference). Nebo můžete použít také [dotnet msbuild](dotnet-msbuild.md) příkazu.

Spuštění `dotnet build` je ekvivalentní `dotnet msbuild -restore -target:Build`.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Soubor projektu nebo řešení pro sestavení. Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí *proj* nebo *sln* a použije tento soubor.

## <a name="options"></a>Možnosti

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Zkompiluje pro konkrétní [framework](../../standard/frameworks.md). Rozhraní musí být definován v [soubor projektu](csproj.md).

* **`--force`**

  Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru. Tato možnost je k dispozici, protože .NET Core 2.0 SDK.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--interactive`**

  Povoluje příkazu zastavit a počkat na vstup uživatele nebo akce. Například k dokončení ověřování. Tato možnost je k dispozici, protože .NET Core 3.0 SDK.

* **`--no-dependencies`**

  Pouze sestavení projektu zadaný kořenový a ignoruje odkazy typu projekt projekt (P2P).

* **`--no-incremental`**

  Označí sestavení jako problematické pro přírůstkové sestavení. Tento příznak vypne přírůstková kompilace a vynutí opětovné čisté sestavení grafu závislostí projektu.

* **`--no-logo`**

  Nezobrazí úvodní nápis a zprávu o autorských právech. Tato možnost je k dispozici, protože .NET Core 3.0 SDK.

* **`--no-restore`**

  Neprovede implicitní obnovení během sestavování. Tato možnost je k dispozici, protože .NET Core 2.0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, do kterého chcete sestavené binární soubory. Budete také muset definovat `--framework` při zadání této možnosti. Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Výchozí hodnota je `minimal`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Nastaví hodnotu vlastnosti `$(VersionSuffix)` vlastnost použít při vytváření projektu. Toto funguje, pouze pokud `$(Version)` není nastavena vlastnost. Potom `$(Version)` je nastavena na `$(VersionPrefix)` v kombinaci s `$(VersionSuffix)`, oddělená spojovníkem.

## <a name="examples"></a>Příklady

* Sestavení projektu a jeho závislosti:

  ```console
  dotnet build
  ```

* Sestavení projektu a jeho závislosti pomocí konfigurace vydané verze:

  ```console
  dotnet build --configuration Release
  ```

* Sestavení projektu a jeho závislosti pro konkrétní prostředí runtime (v tomto příkladu Ubuntu 18.04):

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Sestavte projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2.0 SDK a novější):

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Sestavte projekt a nastavte 1.2.3.4 verzi jako parametr sestavení:

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
