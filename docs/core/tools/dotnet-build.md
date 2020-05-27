---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 02/14/2020
ms.openlocfilehash: 5375df61dbf8e9b4db8772b0e2767e9bca0bb254
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840907"
---
# <a name="dotnet-build"></a>dotnet build

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Name

`dotnet build`– Sestavení projektu a všech jeho závislostí.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>Popis

`dotnet build`Příkaz vytvoří projekt a jeho závislosti do sady binárních souborů. Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* .  V závislosti na typu projektu a nastavení může být zahrnutých dalších souborů, například:

- Spustitelný soubor, který lze použít ke spuštění aplikace, pokud je typ projektu spustitelný soubor cílící na rozhraní .NET Core 3,0 nebo novější.
- Soubory symbolů používané pro ladění s příponou *. pdb* .
- Soubor *. DEPS. JSON* , který obsahuje závislosti aplikace nebo knihovny.
- Soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime a jeho verzi pro aplikaci.
- Další knihovny, na kterých projekt závisí (prostřednictvím odkazů na projekt nebo odkazů na balíček NuGet).

U spustitelných projektů, které cílí na verze starší než .NET Core 3,0, se obvykle nekopírují závislosti knihoven z NuGet do výstupní složky.  Jsou vyřešeny ze složky globálních balíčků NuGet v době běhu. V takovém případě produkt `dotnet build` není připravený k přenosu na jiný počítač ke spuštění. Chcete-li vytvořit verzi aplikace, kterou lze nasadit, je nutné ji publikovat (například pomocí příkazu [dotnet Publish](dotnet-publish.md) ). Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Pro spustitelné projekty cílené na .NET Core 3,0 a novější se závislosti knihoven zkopírují do výstupní složky. To znamená, že pokud neexistují žádné jiné logiky specifické pro publikování (například webové projekty), měl by být výstup sestavení nasazený.

### <a name="implicit-restore"></a>Implicitní obnovení

Sestavování vyžaduje soubor *Project. assets. JSON* , který obsahuje závislosti vaší aplikace. Soubor se vytvoří při [`dotnet restore`](dotnet-restore.md) spuštění. Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a>Výstup spustitelného souboru nebo knihovny

Zda je projekt spustitelný nebo není určen `<OutputType>` vlastností v souboru projektu. Následující příklad ukazuje projekt, který vytváří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Chcete-li vytvořit knihovnu, vynechejte `<OutputType>` vlastnost nebo změňte její hodnotu na `Library` . Knihovna DLL IL pro knihovnu neobsahuje vstupní body a nelze ji spustit.

### <a name="msbuild"></a>MSBuild

`dotnet build`pomocí nástroje MSBuild sestaví projekt, takže podporuje paralelní i přírůstkové sestavení. Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).

Kromě možností `dotnet build` příkaz akceptuje možnosti nástroje MSBuild, například `-p` pro nastavení vlastností nebo pro `-l` Definování protokolovacího nástroje. Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .

Spuštění `dotnet build` je ekvivalentní se spuštěným `dotnet msbuild -restore` . výchozí podrobností výstupu se však liší.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, který se má sestavit Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro většinu projektů je `Debug` , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md). Rozhraní musí být definováno v [souboru projektu](csproj.md).

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.

- **`--no-incremental`**

  Označí sestavení jako nebezpečná pro přírůstkové sestavení. Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.

- **`--no-restore`**

  Během sestavování neprovede implicitní obnovení.

- **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, do kterého se umístí sestavené binární soubory. Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/` .  Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` Vlastnosti) musíte definovat i `--framework` při zadání této možnosti.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

- **`-s|--source <SOURCE>`**

  Identifikátor URI zdroje balíčku NuGet, který má být použit během operace obnovení.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` . Výchozí formát je `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Nastaví hodnotu `$(VersionSuffix)` vlastnosti, která má být použita při sestavování projektu. To funguje pouze v případě, že `$(Version)` vlastnost není nastavena. Pak `$(Version)` je nastaven na `$(VersionPrefix)` kombinaci s `$(VersionSuffix)` oddělovačem odděleným pomlčkou.

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

- Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí `-p` [Možnosti MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
