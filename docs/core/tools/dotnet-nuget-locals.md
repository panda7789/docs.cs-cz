---
title: dotnet nuget locals, příkaz
description: Dotnet nuget locals příkaz vymaže nebo uvádí místní nugetové prostředky, jako je například mezipaměť požadavků http, dočasná mezipaměť nebo globální složky globálních balíčků pro celý počítač.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 5b421b5058528a93c7be58eef2932937cc9cc12d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463536"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze

## <a name="name"></a>Název

`dotnet nuget locals`- Vymaže nebo zobrazí seznam místních prostředků NuGet.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]

dotnet nuget locals -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet nuget locals` vymaže nebo zobrazí seznam místních prostředků NuGet ve složce http-request cache, temporary cache nebo global packages pro celý počítač.

## <a name="arguments"></a>Argumenty

- **`CACHE_LOCATION`**

  Umístění mezipaměti do seznamu nebo vymazání. Přijímá jednu z následujících hodnot:

  * `all`- Označuje, že zadaná operace je použita pro všechny typy mezipaměti: http-request cache, globální balíčky mezipaměti a dočasné mezipaměti.
  * `http-cache`- Označuje, že zadaná operace je použita pouze pro mezipaměť požadavků http. Ostatní umístění mezipaměti nejsou ovlivněny.
  * `global-packages`- Označuje, že zadaná operace je použita pouze pro globální mezipaměti balíčků. Ostatní umístění mezipaměti nejsou ovlivněny.
  * `temp`- Označuje, že zadaná operace je použita pouze pro dočasnou mezipaměť. Ostatní umístění mezipaměti nejsou ovlivněny.

## <a name="options"></a>Možnosti

- **`--force-english-output`**

  Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`-c|--clear`**

  Možnost vymazání provede jasnou operaci u zadaného typu mezipaměti. Obsah adresářů mezipaměti jsou odstraněny rekurzivně. Vykonávající uživatel nebo skupina musí mít oprávnění k souborům v adresářích mezipaměti. Pokud tomu tak není, zobrazí se chyba označující soubory nebo složky, které nebyly vymazány.

- **`-l|--list`**

  Možnost seznamu se používá k zobrazení umístění zadaného typu mezipaměti.

## <a name="examples"></a>Příklady

- Zobrazí cesty všech adresářů místní mezipaměti (adresář http-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Zobrazí cestu k místnímu adresáři http-cache:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář http-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Vymaže všechny soubory v adresáři mezipaměti místních globálních balíčků:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Vymaže všechny soubory v místním adresáři dočasné mezipaměti:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Řešení potíží

Informace o běžných problémech `dotnet nuget locals` a chybách při použití příkazu naleznete v [tématu Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).
