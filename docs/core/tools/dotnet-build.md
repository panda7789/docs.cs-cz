---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 10/14/2019
ms.openlocfilehash: b85ef06aa445e4708487deed9ec6bfeffeab3657
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454214"
---
# <a name="dotnet-build"></a>dotnet build

**Tento článek se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet build` – sestavení projektu a všech jeho závislostí.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo] 
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet build` sestaví projekt a jeho závislosti do sady binárních souborů. Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* .  V závislosti na typu projektu a nastavení může být zahrnutých dalších souborů, například:

- Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelný soubor cílící na rozhraní .NET Core 3,0 nebo novější.
- Soubory symbolů používané pro ladění s příponou *. pdb* .
- Soubor *. DEPS. JSON* , který obsahuje závislosti aplikace nebo knihovny.
- Soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime a jeho verzi pro aplikaci.
- Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).

U spustitelných projektů, které cílí na verze starší než .NET Core 3,0, se obvykle nekopírují závislosti knihoven z NuGet do výstupní složky.  Jsou vyřešeny ze složky globálních balíčků NuGet v době běhu. V takovém případě produkt `dotnet build` není připraven k přenosu do jiného počítače ke spuštění. Chcete-li vytvořit verzi aplikace, kterou lze nasadit, je nutné ji publikovat (například pomocí příkazu [dotnet Publish](dotnet-publish.md) ). Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Pro spustitelné projekty cílené na .NET Core 3,0 a novější se závislosti knihoven zkopírují do výstupní složky. To znamená, že pokud neexistují žádné jiné logiky specifické pro publikování (například webové projekty), měl by být výstup sestavení nasazený.

Sestavování vyžaduje soubor *Project. assets. JSON* , který obsahuje závislosti vaší aplikace. Soubor se vytvoří při spuštění [`dotnet restore`](dotnet-restore.md) . Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby. Pomocí sady .NET Core 1. x SDK jste před spuštěním `dotnet build` museli explicitně spustit `dotnet restore`. Počínaje verzí .NET Core 2,0 SDK se `dotnet restore` spouští implicitně při spuštění `dotnet build`. Pokud chcete zakázat implicitní obnovení při spuštění příkazu Build, můžete předat možnost `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Zda je projekt spustitelný nebo není určen vlastností `<OutputType>` v souboru projektu. Následující příklad ukazuje projekt, který vytváří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Chcete-li vytvořit knihovnu, vynechejte vlastnost `<OutputType>` nebo změňte její hodnotu na `Library`. Knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ji spustit.

### <a name="msbuild"></a>MSBuild

`dotnet build` používá nástroj MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení. Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).

Kromě možností příkaz `dotnet build` přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností nebo `-l` pro definování protokolovacího nástroje. Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .

Spuštění `dotnet build` je ekvivalentem spuštění `dotnet msbuild -restore`; výchozí podrobnost výstupu se ale liší.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, který se má sestavit Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.

## <a name="options"></a>Možnosti

- **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md). Rozhraní musí být definováno v [souboru projektu](csproj.md).

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* . K dispozici od verze .NET Core 2,0 SDK.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.

- **`--no-incremental`**

  Označí sestavení jako nebezpečná pro přírůstkové sestavení. Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.

- **`--no-restore`**

  Během sestavování neprovede implicitní obnovení. K dispozici od verze .NET Core 2,0 SDK.

- **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, do kterého se umístí sestavené binární soubory. Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.  Pro projekty s více cílovými rozhraními (prostřednictvím vlastnosti `TargetFrameworks`) je také potřeba definovat `--framework` při zadání této možnosti.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`. Výchozí hodnota je `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Nastaví hodnotu vlastnosti `$(VersionSuffix)`, která se má použít při sestavování projektu. To funguje pouze v případě, že vlastnost `$(Version)` není nastavena. Pak `$(Version)` se nastaví na `$(VersionPrefix)` kombinované s `$(VersionSuffix)` oddělené pomlčkou.

## <a name="examples"></a>Příklady

- Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet build
  ```

- Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Sestavení projektu a jeho závislostí pro určitý modul runtime (v tomto příkladu Ubuntu 18,04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Sestavit projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2,0 SDK a novější verze):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí možnosti `-p` [MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
