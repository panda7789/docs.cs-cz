---
title: příkaz dotnet list Package
description: Příkaz dotnet list Package nabízí pohodlný možnost zobrazit seznam odkazů na balíčky pro projekt nebo řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157229"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Tento článek se týká:** ✔️ .net Core 2,2 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet list package` – obsahuje odkazy na balíček pro projekt nebo řešení.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet list package` nabízí pohodlný možnost zobrazit seznam všech odkazů na balíčky NuGet pro konkrétní projekt nebo řešení. Nejprve je třeba sestavit projekt, aby bylo možné pro tento příkaz zpracovat potřebné prostředky. Následující příklad ukazuje výstup příkazu `dotnet list package` pro projekt [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Požadovaný** sloupec odkazuje na verzi balíčku zadanou v souboru projektu a může být rozsahem. Sloupec **vyřešený** obsahuje verzi, kterou projekt aktuálně používá, a je vždy jednou hodnotou. Balíčky zobrazující `(A)` vpravo vedle jejich názvů představují [Implicitní odkazy na balíčky](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (typ`Sdk`, `<TargetFramework>` nebo `<TargetFrameworks>` Property atd.).

Pomocí možnosti `--outdated` zjistíte, jestli jsou v projektech k dispozici novější verze balíčků, které používáte. Ve výchozím nastavení `--outdated` uvádí nejnovější stabilní balíčky, pokud není přeložená verze zároveň předprodejní verze. Chcete-li zahrnout předprodejní verze při výpisu novějších verzí, zadejte také možnost `--include-prerelease`. Následující příklady ukazují výstup příkazu `dotnet list package --outdated --include-prerelease` pro stejný projekt jako předchozí příklad:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Pokud potřebujete zjistit, zda má váš projekt přenositelné závislosti, použijte možnost `--include-transitive`. K přenosným závislostem dochází při přidávání balíčku do projektu, který se následně spoléhá na jiný balíček. Následující příklad ukazuje výstup z spuštění příkazu `dotnet list package --include-transitive` pro projekt [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých jsou závislé:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, na kterém chcete pracovat. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud se najde více než jedno řešení nebo projekt, vyvolá se chyba.

## <a name="options"></a>Možnosti

- **`--config <SOURCE>`**

  Zdroje NuGet, které se mají použít při hledání novějších balíčků Vyžaduje možnost `--outdated`.

- **`--framework <FRAMEWORK>`**

  Zobrazí jenom balíčky, které platí pro zadanou [cílovou architekturu](../../standard/frameworks.md). Pokud chcete zadat více platforem, opakujte možnost několikrát. Například: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--highest-minor`**

  Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacím číslem hlavní verze. Vyžaduje možnost `--outdated`.

- **`--highest-patch`**

  Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacími čísly hlavní verze a podverze. Vyžaduje možnost `--outdated`.

- **`--include-prerelease`**

  Při hledání novějších balíčků bere v úvahu balíčky s předběžnou verzí. Vyžaduje možnost `--outdated`.

- **`--include-transitive`**

  Vypisuje přenositelné balíčky kromě balíčků nejvyšší úrovně. Když zadáte tuto možnost, zobrazí se seznam balíčků, na kterých jsou závislé balíčky na nejvyšší úrovni.

- **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`--outdated`**

  Vypíše balíčky s dostupnými novějšími verzemi.

- **`-s|--source <SOURCE>`**

  Zdroje NuGet, které se mají použít při hledání novějších balíčků Vyžaduje možnost `--outdated`.

## <a name="examples"></a>Příklady

- Výpis odkazů na balíčky určitého projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Vypíše odkazy na balíčky s dostupnými novějšími verzemi, včetně předprodejních verzí:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Vypíše odkazy na balíčky pro konkrétní cílové rozhraní:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
