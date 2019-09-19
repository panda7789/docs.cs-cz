---
title: příkaz dotnet list Package
description: Příkaz dotnet list Package nabízí pohodlný možnost zobrazit seznam odkazů na balíčky pro projekt nebo řešení.
ms.date: 06/26/2019
ms.openlocfilehash: fe95f3898c5bd85956f4312eb4d20259227e9ff0
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117725"
---
# <a name="dotnet-list-package"></a>dotnet list package

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Name

`dotnet list package`– Obsahuje odkazy na balíčky pro projekt nebo řešení.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Popis

`dotnet list package` Příkaz nabízí pohodlný možnost zobrazit seznam všech odkazů balíčků NuGet pro konkrétní projekt nebo řešení. Nejprve je třeba sestavit projekt, aby bylo možné pro tento příkaz zpracovat potřebné prostředky. Následující příklad ukazuje výstup `dotnet list package` příkazu pro projekt [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Požadovaný** sloupec odkazuje na verzi balíčku zadanou v souboru projektu a může být rozsahem. Sloupec **vyřešený** obsahuje verzi, kterou projekt aktuálně používá, a je vždy jednou hodnotou. Balíčky zobrazující `(A)` právo vedle jejich názvů představují [Implicitní odkazy na balíčky](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (`Sdk` typ, `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost atd.).

`--outdated` Pomocí možnosti zjistíte, jestli jsou v projektech k dispozici novější verze balíčků, které používáte. Ve výchozím nastavení `--outdated` zobrazí seznam nejnovějších stabilních balíčků, pokud není přeložená verze zároveň předprodejní verze. Pokud chcete při výpisu novějších verzí zahrnout předběžné verze, zadejte `--include-prerelease` také možnost. Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` příkazu pro stejný projekt jako předchozí příklad:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Pokud potřebujete zjistit, zda má váš projekt přenositelné závislosti, použijte `--include-transitive` možnost. K přenosným závislostem dochází při přidávání balíčku do projektu, který se následně spoléhá na jiný balíček. Následující příklad ukazuje výstup z spuštění `dotnet list package --include-transitive` příkazu pro projekt [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých jsou závislé:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, na kterém chcete pracovat. Pokud není zadán, příkaz vyhledá v aktuálním adresáři. Pokud se najde více než jedno řešení nebo projekt, vyvolá se chyba.

## <a name="options"></a>Možnosti

* **`--config <SOURCE>`**

  Zdroje NuGet, které se mají použít při hledání novějších balíčků `--outdated` Vyžaduje možnost.

* **`--framework <FRAMEWORK>`**

  Zobrazí jenom balíčky, které platí pro zadanou [cílovou architekturu](../../standard/frameworks.md). Pokud chcete zadat více platforem, opakujte možnost několikrát. Například: `--framework netcoreapp2.2 --framework netstandard2.0`.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`--highest-minor`**

  Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacím číslem hlavní verze. `--outdated` Vyžaduje možnost.

* **`--highest-patch`**

  Při hledání novějších balíčků bere v úvahu jenom balíčky s porovnávacími čísly hlavní verze a podverze. `--outdated` Vyžaduje možnost.

* **`--include-prerelease`**

  Při hledání novějších balíčků bere v úvahu balíčky s předběžnou verzí. `--outdated` Vyžaduje možnost.

* **`--include-transitive`**

  Vypisuje přenositelné balíčky kromě balíčků nejvyšší úrovně. Když zadáte tuto možnost, zobrazí se seznam balíčků, na kterých jsou závislé balíčky na nejvyšší úrovni.

* **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

* **`--outdated`**

  Vypíše balíčky s dostupnými novějšími verzemi.

* **`-s|--source <SOURCE>`**

  Zdroje NuGet, které se mají použít při hledání novějších balíčků `--outdated` Vyžaduje možnost.

## <a name="examples"></a>Příklady

* Výpis odkazů na balíčky určitého projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

* Vypíše odkazy na balíčky s dostupnými novějšími verzemi, včetně předprodejních verzí:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

* Vypíše odkazy na balíčky pro konkrétní cílové rozhraní:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
