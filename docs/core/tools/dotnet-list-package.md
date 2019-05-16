---
title: příkaz DotNet seznamu balíčků
description: Příkaz "balíčku dotnet seznamu" poskytuje vhodnou možnost zobrazíte odkazy na balíčky pro projekt nebo řešení.
ms.date: 04/09/2019
ms.openlocfilehash: 88ef3302a955eadc4167384312e4eb721dd496fb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631767"
---
# <a name="dotnet-list-package"></a>DotNet seznamu balíčků

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Name

`dotnet list package` -Obsahuje odkazy na balíčky pro projekt nebo řešení.

## <a name="synopsis"></a>Souhrn

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Popis

`dotnet list package` Příkaz poskytuje vhodnou možnost vypsat všechny odkazy na balíčky NuGet pro konkrétní projekt nebo řešení. Musíte nejprve sestavte projekt, aby měla prostředky potřebné pro tento příkaz zpracovat. Následující příklad ukazuje výstup `dotnet list package` příkazu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Požadovaná** sloupec odkazuje na balíček verze zadaná v souboru projektu a mohou být rozsah. **Vyřešeno** sloupce se zobrazí výpis verze, že projekt je aktuálně používá a je vždy jedna hodnota. Balíčky zobrazení `(A)` představují vpravo vedle jejich názvů [odkazy na balíček implicitní](csproj.md#implicit-package-references) , které jsou odvozeny z nastavení projektu (`Sdk` typ `<TargetFramework>` nebo `<TargetFrameworks>` vlastnost atd.)

Použití `--outdated` možnost zjistit, existuje novější verze balíčků, které používáte ve svých projektech. Ve výchozím nastavení `--outdated` uvádí nejnovější stabilní balíčky, není-li vyřešit verze je také Předběžná verze. Chcete-li zahrnout předběžné verze při výpisu novější verze, určit `--include-prerelease` možnost. Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` stejný projekt jako předchozí příklad příkazu:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Pokud potřebujete zjistit, zda má váš projekt přechodné závislosti, použijte `--include-transitive` možnost. Přechodné závislosti dojít, když přidáte balíček do projektu, která zase závisí na jiném balíčku. Následující příklad ukazuje výstup z běžící `dotnet list package --include-transitive` příkazu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projekt, který zobrazí nejvyšší úrovně balíčky a balíčky, které jsou závislé na:

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

Soubor projektu nebo řešení se má operace provést. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden. Pokud je nalezen více než jedno řešení nebo projekt, je vržena chyba.

## <a name="options"></a>Možnosti

* **`--config <SOURCE>`**

  NuGet zdroje, které chcete použít při hledání novější balíčky. Vyžaduje `--outdated` možnost.

* **`--framework <FRAMEWORK>`**

  Zobrazí jenom balíčky použitelné pro zadaný rozbočovač [Cílová architektura](../../standard/frameworks.md). Chcete-li zadat více platforem, opakujte možnost více než jednou. Například: `--framework netcoreapp2.2 --framework netstandard2.0`.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--highest-minor`**

  Bere v úvahu jenom balíčky s odpovídající číslo hlavní verze vyhledávání novější balíčky. Vyžaduje `--outdated` možnost.

* **`--highest-patch`**

  Bere v úvahu jenom balíčky k odpovídajícímu hlavní a podverze čísla při hledání novější balíčky. Vyžaduje `--outdated` možnost.

* **`--include-prerelease`**

  Při hledání novější balíčky bere v úvahu balíčky s předběžné verze. Vyžaduje `--outdated` možnost.

* **`--include-transitive`**

  Zobrazí seznam tranzitivní balíčků, kromě nejvyšší úrovně balíčky. Při zadání této možnosti, získání seznamu balíčků, které závisí nejvyšší úrovni balíčky.

* **`--outdated`**

  Zobrazí seznam balíčků, které mají k dispozici novější verze.

* **`-s|--source <SOURCE>`**

  NuGet zdroje, které chcete použít při hledání novější balíčky. Vyžaduje `--outdated` možnost.

## <a name="examples"></a>Příklady

* Seznam odkazů balíček na určitém projektu:

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* Seznam odkazy na balíčky, které mají novější verze, které jsou k dispozici, včetně předběžné verze:

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* Vypište odkazy na balíček pro konkrétní cílové rozhraní:

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
