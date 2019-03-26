---
title: příkaz DotNet pack
description: Příkaz dotnet pack vytvoří balíčky NuGet pro projekt .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: 4b665140f7c660c5851fb68b07ecec2d9391b925
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464473"
---
# <a name="dotnet-pack"></a>balíčku DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet pack` -Sbalit kód do balíčku NuGet.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet pack` Příkaz sestaví projekt a vytváří balíčky NuGet. Výsledek tohoto příkazu je balíček NuGet. Pokud `--include-symbols` možnost je k dispozici, je vytvořen jiný balíček, který obsahuje symboly ladění.

Závislostí NuGet komprimovat komprimovaný objekt projektu jsou přidány do *souboru .nuspec* souboru, aby byly správně přeložit, při instalaci balíčku. Odkazy typu projekt projekt nejsou zabaleny v projektu. V současné době musí mít balíček na projekt, pokud máte závislosti projektu k projektu.

Ve výchozím nastavení `dotnet pack` nejprve sestaví projekt. Pokud chcete-li toto chování vyhnout, předejte `--no-build` možnost. Tato možnost je často užitečné pro scénáře sestavení kontinuální integrace (CI), kdy víte, že kód byl vytvořen dříve.

Můžete zadat vlastnosti nástroje MSBuild k `dotnet pack` příkaz pro proces balení. Další informace najdete v tématu [vlastnosti metadat NuGet](csproj.md#nuget-metadata-properties) a [MSBuild Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference). [Příklady](#examples) části ukazuje, jak pomocí přepínače -p MSBuild pro několik různých scénářů.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Projekt se zabalit. Je buď cestu k [souboru csproj](csproj.md) nebo do adresáře. Pokud není zadán, použije se výchozí do aktuálního adresáře.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`--force`**

  Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--include-source`**

  Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.

* **`--include-symbols`**

  Vygeneruje symboly `nupkg`.

* **`--no-build`**

  Nelze sestavit projekt před balení. Také implicitně nastaví `--no-restore` příznak.

* **`--no-dependencies`**

  Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.

* **`--no-restore`**

  Při spuštění příkazu se nebude spouštět implicitní obnovení.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí sestavené balíčky v adresáři uvedeném.

* **`--runtime <RUNTIME_IDENTIFIER>`**

  Určuje cílový modul runtime pro obnovování balíčků pro. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

* **`-s|--serviceable`**

  Nastaví příznak nacházet v balíčku. Další informace najdete v tématu [Blog k .NET: .NET 4.5.1 aktualizace zabezpečení Microsoftu podporuje pro NuGet knihovny .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu pro `$(VersionSuffix)` vlastnost MSBuild v projektu.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

> [!NOTE]
> Webové projekty nejsou packable ve výchozím nastavení. Pokud chcete přepsat výchozí chování, přidejte následující vlastnost, která má vaše *.csproj* souboru:
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--include-source`**

  Obsahuje zdrojové soubory v balíčku NuGet. Zdrojové soubory jsou součástí `src` složky v rámci `nupkg`.

* **`--include-symbols`**

  Vygeneruje symboly `nupkg`.

* **`--no-build`**

  Nelze sestavit projekt před balení.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístí sestavené balíčky v adresáři uvedeném.

* **`-s|--serviceable`**

  Nastaví příznak nacházet v balíčku. Další informace najdete v tématu [Blog k .NET: .NET 4.5.1 aktualizace zabezpečení Microsoftu podporuje pro NuGet knihovny .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definuje hodnotu pro `$(VersionSuffix)` vlastnost MSBuild v projektu.

* **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

---

## <a name="examples"></a>Příklady

* Sada projekt v aktuálním adresáři:

  ```console
  dotnet pack
  ```

* Balíček `app1` projektu:

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* Zabalit projekt v aktuálním adresáři a umístí výsledný balíčky do `nupkgs` složky:

  ```console
  dotnet pack --output nupkgs
  ```

* Sbalení projekt v aktuálním adresáři, do `nupkgs` složky a přeskočit krok sestavení:

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* S projektem verze příponu nakonfigurovaná jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` v *.csproj* souborů, aktuální projekt pack a aktualizovaných výsledný verze balíčku s danou příponou:

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* Nastavte verzi balíčku `2.1.0` s `PackageVersion` vlastnost MSBuild:

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* Projekt pro konkrétní Pack [Cílová architektura](../../standard/frameworks.md):

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* Zabalte projektu a použití konkrétního modulu runtime (Windows 10) pro operaci obnovení (.NET Core SDK 2.0 a novější):

  ```console
  dotnet pack --runtime win10-x64
  ```

* Pack projekt pomocí [soubor souboru .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```console
  dotnet pack  ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
