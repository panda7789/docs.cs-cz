---
title: dotnet – místní příkazy NuGet
description: Příkaz dotnet NuGet Locals vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503692"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Název

`dotnet nuget locals` – vymaže nebo vypíše místní prostředky NuGet.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget locals` vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku HTTP, dočasné mezipaměti nebo v rámci globální složky balíčků v celém počítači.

## <a name="arguments"></a>Argumenty

- **`CACHE_LOCATION`**

  Umístění mezipaměti, které se má vypsat nebo vymazat Přijímá jednu z následujících hodnot:

  * `all` – určuje, že zadaná operace se použije pro všechny typy mezipaměti: mezipaměť požadavků HTTP, mezipaměť globálních balíčků a dočasná mezipaměť.
  * `http-cache` – určuje, že zadaná operace se použije jenom pro mezipaměť http požadavku. Ostatní umístění mezipaměti nejsou ovlivněna.
  * `global-packages` – určuje, že zadaná operace se použije jenom pro mezipaměť globálních balíčků. Ostatní umístění mezipaměti nejsou ovlivněna.
  * `temp` – určuje, že zadaná operace se použije jenom pro dočasnou mezipaměť. Ostatní umístění mezipaměti nejsou ovlivněna.

## <a name="options"></a>Možnosti

- **`--force-english-output`**

  Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`-c|--clear`**

  Možnost Clear spustí u zadaného typu mezipaměti operaci Clear. Obsah adresářů mezipaměti se odstraní rekurzivně. Spuštěný uživatel nebo skupina musí mít oprávnění k souborům v adresářích mezipaměti. V takovém případě se zobrazí chyba označující soubory nebo složky, které nebyly vymazány.

- **`-l|--list`**

  Možnost seznam slouží k zobrazení umístění zadaného typu mezipaměti.

## <a name="examples"></a>Příklady

- Zobrazuje cesty ke všem adresářům místní mezipaměti (adresář HTTP-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Zobrazuje cestu k místnímu adresáři protokolu HTTP-cache:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu HTTP, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Vymaže všechny soubory v místní složce mezipaměti Global-Packages:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Vymaže všechny soubory v adresáři místní dočasné mezipaměti:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Řešení potíží

Informace o běžných problémech a chybách při použití příkazu `dotnet nuget locals` najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).
