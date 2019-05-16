---
title: příkaz DotNet nuget místních hodnot
description: Příkaz dotnet nuget locals vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 0a9fd7876aa4d1907eb37e6bac54295d938d36d3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632427"
---
# <a name="dotnet-nuget-locals"></a>DotNet nuget locals

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet nuget locals` -Vymaže nebo vypíše místní prostředky NuGet.

## <a name="synopsis"></a>Souhrn

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Popis

`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Umístění mezipaměti seznamu nebo zrušte zaškrtnutí. Přijímá jednu z následujících hodnot:

  * `all` – Označuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměť požadavku http, mezipaměť globálních balíčků a dočasná mezipaměť.
  * `http-cache` -Označuje, že zadaná operace je použit pouze pro mezipaměť požadavku http. Jiné umístění mezipaměti nejsou ovlivněny.
  * `global-packages` -Označuje, že zadaná operace platí pouze pro mezipaměť globálních balíčků. Jiné umístění mezipaměti nejsou ovlivněny.
  * `temp` -Označuje, že zadaná operace platí jenom pro dočasná mezipaměť. Jiné umístění mezipaměti nejsou ovlivněny.

## <a name="options"></a>Možnosti

* **`--force-english-output`**

  Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`-c|--clear`**

  Zrušte zaškrtnutí možnost provede operaci zrušte na typ zadaný mezipaměti. Obsah adresáře mezipaměti jsou odstraněné rekurzivně. Provádění uživatele nebo skupiny musí mít oprávnění k souborům v adresářích mezipaměti. Pokud tomu tak není, zobrazí se chyba, která souborů a složek, které nebyly vymazány.

* **`-l|--list`**

  Možnost seznamu se používá k zobrazení umístění mezipaměti zadaného typu.

## <a name="examples"></a>Příklady

* Zobrazuje cesty ke všem adresářům místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):

  ```console
  dotnet nuget locals –l all
  ```

* Zobrazuje cestu k adresáři místní mezipaměť http:

  ```console
  dotnet nuget locals --list http-cache
  ```

* Vymaže všechny soubory z adresáře všechny místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):

  ```console
  dotnet nuget locals --clear all
  ```

* Vymaže všechny soubory v adresáři místního global-packages mezipaměti:

  ```console
  dotnet nuget locals -c global-packages
  ```

* Vymaže všechny soubory v adresáři místní dočasné mezipaměti:

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Poradce při potížích

Informace o běžných problémech a chyb při použití `dotnet nuget locals` naleznete [Správa mezipaměti Nugetu](/nuget/consume-packages/managing-the-nuget-cache).
