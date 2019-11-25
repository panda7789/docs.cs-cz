---
title: dotnet – místní příkazy NuGet
description: Příkaz dotnet NuGet Locals vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: cb5747636aa9d04f1ef6a6ff9309ba29c0630dd6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087408"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget locals` – vymaže nebo vypíše místní prostředky NuGet.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget locals` vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku HTTP, dočasné mezipaměti nebo v rámci globální složky balíčků v celém počítači.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Umístění mezipaměti, které se má vypsat nebo vymazat Přijímá jednu z následujících hodnot:

  * `all` – určuje, že zadaná operace se použije pro všechny typy mezipaměti: mezipaměť požadavků HTTP, mezipaměť globálních balíčků a dočasná mezipaměť.
  * `http-cache` – určuje, že zadaná operace se použije jenom pro mezipaměť http požadavku. Ostatní umístění mezipaměti nejsou ovlivněna.
  * `global-packages` – určuje, že zadaná operace se použije jenom pro mezipaměť globálních balíčků. Ostatní umístění mezipaměti nejsou ovlivněna.
  * `temp` – určuje, že zadaná operace se použije jenom pro dočasnou mezipaměť. Ostatní umístění mezipaměti nejsou ovlivněna.

## <a name="options"></a>Možnosti

* **`--force-english-output`**

  Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

* **`-c|--clear`**

  Možnost Clear spustí u zadaného typu mezipaměti operaci Clear. Obsah adresářů mezipaměti se odstraní rekurzivně. Spuštěný uživatel nebo skupina musí mít oprávnění k souborům v adresářích mezipaměti. V takovém případě se zobrazí chyba označující soubory nebo složky, které nebyly vymazány.

* **`-l|--list`**

  Možnost seznam slouží k zobrazení umístění zadaného typu mezipaměti.

## <a name="examples"></a>Příklady

* Zobrazuje cesty ke všem adresářům místní mezipaměti (adresář HTTP-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

* Zobrazuje cestu k místnímu adresáři protokolu HTTP-cache:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu HTTP, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* Vymaže všechny soubory v místní složce mezipaměti Global-Packages:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* Vymaže všechny soubory v adresáři místní dočasné mezipaměti:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Poradce při potížích

Informace o běžných problémech a chybách při použití příkazu `dotnet nuget locals` najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).
