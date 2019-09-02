---
title: příkaz dotnet Pack
description: Příkaz dotnet Pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202841"
---
# <a name="dotnet-pack"></a>dotnet pack

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet pack`– Zabalí kód do balíčku NuGet.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet pack` Příkaz sestaví projekt a vytvoří balíčky NuGet. Výsledek tohoto příkazu je balíček NuGet. Pokud je `--include-symbols` Tato možnost k dispozici, je vytvořen jiný balíček obsahující symboly ladění.

Do souboru *. nuspec* jsou přidány závislosti NuGet zkomprimovaného projektu, aby byly po instalaci balíčku správně vyřešeny. Odkazy z projektu na projekt nejsou zabaleny do projektu. V současné době je nutné mít balíček na projekt, pokud máte závislosti typu projekt-projekt.

Ve výchozím nastavení `dotnet pack` sestaví projekt jako první. Pokud se chcete tomuto chování vyhnout, předejte `--no-build` možnost. Tato možnost je často užitečná ve scénářích průběžné integrace (CI), kde víte, že kód byl dříve sestaven.

Vlastnosti nástroje MSBuild můžete zadat pro `dotnet pack` příkaz pro proces balení. Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [Reference k příkazovému řádku MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). V části s [Příklady](#examples) se dozvíte, jak použít přepínač MSBuild-p pro několik různých scénářů.

Webové projekty nejsou ve výchozím nastavení nabaleny. Chcete-li přepsat výchozí chování, přidejte do souboru *. csproj* následující vlastnost:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Projekt, který se má zabalit Jedná se buď o cestu k [souboru csproj](csproj.md) , nebo k adresáři. Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--include-source`**

  Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou zahrnuty ve `src` složce v `nupkg`rámci.

* **`--include-symbols`**

  Vygeneruje symboly `nupkg`.

* **`--no-build`**

  Nevytvoří projekt před balením. Také implicitně nastaví `--no-restore` příznak.

* **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.

* **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí sestavené balíčky do zadaného adresáře.

* **`--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime pro obnovení balíčků pro. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).

* **`-s|--serviceable`**

  Nastaví v balíčku příznak služby. Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--include-source`**

  Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou zahrnuty ve `src` složce v `nupkg`rámci.

* **`--include-symbols`**

  Vygeneruje symboly `nupkg`.

* **`--no-build`**

  Nevytvoří projekt před balením.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí sestavené balíčky do zadaného adresáře.

* **`-s|--serviceable`**

  Nastaví v balíčku příznak služby. Další informace najdete na [blogu .NET: rozhraní .NET 4.5.1 podporuje aktualizace zabezpečení Microsoftu pro knihovny NuGet pro .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu `$(VersionSuffix)` vlastnosti MSBuild v projektu.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

---

## <a name="examples"></a>Příklady

* Sbalit projekt v aktuálním adresáři:

  ```console
  dotnet pack
  ```

* `app1` Sbalit projekt:

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* Sbalení projektu v aktuálním adresáři a umístění výsledných balíčků do `nupkgs` složky:

  ```console
  dotnet pack --output nupkgs
  ```

* Sbalení projektu v aktuálním adresáři do `nupkgs` složky a přeskočení kroku sestavení:

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* S příponou verze projektu nakonfigurovanou jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v souboru *. csproj* rozbalte aktuální projekt a aktualizujte výslednou verzi balíčku s danou příponou:

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* Nastavte na verzi `2.1.0` `PackageVersion` balíčku vlastnost MSBuild:

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* Sbalení projektu pro konkrétní [cílové rozhraní](../../standard/frameworks.md):

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* Sbalení projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2,0 a novější verze):

  ```console
  dotnet pack --runtime win10-x64
  ```

* Sbalení projektu pomocí [souboru. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
