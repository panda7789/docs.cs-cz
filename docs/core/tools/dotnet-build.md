---
title: dotnet – příkaz sestavení
description: Příkaz dotnet Build vytvoří projekt a všechny jeho závislosti.
ms.date: 08/08/2019
ms.openlocfilehash: 6194d70a8a14e63adbcad39c7dabbbd220ca329d
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179967"
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
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet build` sestaví projekt a jeho závislosti do sady binárních souborů. Binární soubory obsahují kód projektu v souborech IL (Intermediate Language) s příponou *. dll* a soubory symbolů používané pro ladění s příponou *. pdb* . Vytvoří se soubor JSON závislosti ( *. DEPS. JSON*), který obsahuje seznam závislostí aplikace. Je vytvořen soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime a jeho verzi aplikace.

Pokud má projekt závislosti třetích stran, jako jsou knihovny z NuGet, jsou vyřešeny z mezipaměti NuGet a nejsou k dispozici s vytvořeným výstupem projektu. V takovém případě produkt `dotnet build` není připraven k přenosu do jiného počítače ke spuštění. To je v kontrastu s chováním .NET Framework, při které sestavení spustitelného projektu (aplikace) vytvoří výstup, který je spustitelný na jakémkoli počítači, kde je nainstalován .NET Framework. Chcete-li mít rozhraní .NET Core podobné prostředí, je nutné použít příkaz [dotnet Publish](dotnet-publish.md) . Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

Sestavování vyžaduje soubor *Project. assets. JSON* , který obsahuje závislosti vaší aplikace. Soubor se vytvoří při spuštění [`dotnet restore`](dotnet-restore.md) . Bez zavedeného souboru prostředků nemůže nástroj překládat referenční sestavení, což má za následek chyby. Pomocí sady .NET Core 1. x SDK jste před spuštěním `dotnet build` museli explicitně spustit `dotnet restore`. Počínaje verzí .NET Core 2,0 SDK se `dotnet restore` spouští implicitně při spuštění `dotnet build`. Pokud chcete zakázat implicitní obnovení při spuštění příkazu Build, můžete předat možnost `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Zda je projekt spustitelný nebo není určen vlastností `<OutputType>` v souboru projektu. Následující příklad ukazuje projekt, který vytváří spustitelný kód:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Chcete-li vytvořit knihovnu, vynechejte vlastnost `<OutputType>`. Hlavním rozdílem v sestavení výstupu je, že knihovna DLL IL pro knihovnu neobsahuje vstupní body a nemůže být provedena.

### <a name="msbuild"></a>MSBuild

`dotnet build` používá nástroj MSBuild k sestavení projektu, takže podporuje paralelní i přírůstkové sestavení. Další informace naleznete v tématu [přírůstkové sestavení](/visualstudio/msbuild/incremental-builds).

Kromě možností příkaz `dotnet build` přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností nebo `-l` pro definování protokolovacího nástroje. Další informace o těchto možnostech naleznete v tématu Referenční dokumentace k [příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Případně můžete použít také příkaz [dotnet MSBuild](dotnet-msbuild.md) .

Spuštění `dotnet build` je ekvivalentem `dotnet msbuild -restore -target:Build`.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, který se má sestavit Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá v aktuálním pracovním adresáři soubor s příponou souboru, který končí buď *proj* nebo *sln* , a použije tento soubor.

## <a name="options"></a>Možnosti

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Zkompiluje pro konkrétní [rozhraní](../../standard/frameworks.md). Rozhraní musí být definováno v [souboru projektu](csproj.md).

* **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* . K dispozici od verze .NET Core 2,0 SDK.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

* **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt (P2P) a sestavuje pouze zadaný kořenový projekt.

* **`--no-incremental`**

  Označí sestavení jako nebezpečná pro přírůstkové sestavení. Tento příznak vypne přírůstkovou kompilaci a vynutí čisté opětovné sestavení grafu závislostí projektu.

* **`--no-restore`**

  Během sestavování neprovede implicitní obnovení. K dispozici od verze .NET Core 2,0 SDK.

* **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, do kterého se umístí sestavené binární soubory. I když zadáte tuto možnost, musíte definovat `--framework`. Pokud není zadán, výchozí cesta je `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností MSBuild. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` a `diag[nostic]`. Výchozí hodnota je `minimal`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Nastaví hodnotu vlastnosti `$(VersionSuffix)`, která se má použít při sestavování projektu. To funguje pouze v případě, že vlastnost `$(Version)` není nastavena. Pak `$(Version)` se nastaví na `$(VersionPrefix)` kombinované s `$(VersionSuffix)` oddělené pomlčkou.

## <a name="examples"></a>Příklady

* Sestavení projektu a jeho závislostí:

  ```dotnetcli
  dotnet build
  ```

* Sestavení projektu a jeho závislostí pomocí konfigurace vydané verze:

  ```dotnetcli
  dotnet build --configuration Release
  ```

* Sestavení projektu a jeho závislostí pro určitý modul runtime (v tomto příkladu Ubuntu 18,04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Sestavit projekt a použít zadaný zdroj balíčku NuGet během operace obnovení (.NET Core 2,0 SDK a novější verze):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* Sestavte projekt a nastavte parametr Version 1.2.3.4 jako parametr sestavení pomocí možnosti `-p` [MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
