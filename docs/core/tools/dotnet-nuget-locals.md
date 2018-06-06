---
title: příkaz místní hodnoty – DotNet nuget - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nuget místní hodnoty – vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696868"
---
# <a name="dotnet-nuget-locals"></a>místní hodnoty nuget DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet nuget locals` -Vymaže nebo vypíše místní prostředky NuGet.

## <a name="synopsis"></a>Stručný obsah

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Popis

`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.

## <a name="arguments"></a>Arguments

`CACHE_LOCATION`

Umístění mezipaměti k zobrazení seznamu nebo vymazat. Přijme jeden z následujících hodnot:

* `all` -Určuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměti požadavek http, globální balíčky mezipaměti a dočasnou vyrovnávací paměť.
* `http-cache` -Určuje, že zadaná operace platí pouze do mezipaměti v požadavku http. Ovlivněné nejsou jiných umístění mezipaměti.
* `global-packages` -Určuje, že zadaná operace se aplikuje jenom na globální balíčky mezipaměti. Ovlivněné nejsou jiných umístění mezipaměti.
* `temp` -Určuje, že zadaná operace se aplikuje jenom na dočasnou vyrovnávací paměť. Ovlivněné nejsou jiných umístění mezipaměti.

## <a name="options"></a>Možnosti

`--force-english-output`

Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-c|--clear`

Zrušte možnost provede zrušte operaci na zadaný mezipaměti typu. Obsah mezipaměti adresáře jsou odstraněné rekurzivně. Provádění uživatel nebo skupina musí mít oprávnění k souborům v adresáři mezipaměti. Pokud ne, zobrazí se chybová zpráva označující, soubory a složky, které nejsou vymazána.

`-l|--list`

V seznamu možnost se používá pro zobrazení umístění mezipaměti zadaného typu.

## <a name="examples"></a>Příklady

Zobrazí cesty všechny adresáře místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):

`dotnet nuget locals –l all`

Zobrazuje cestu k adresáři místní mezipaměti http:

`dotnet nuget locals --list http-cache`

Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):

`dotnet nuget locals --clear all`

Vymaže všechny soubory v adresáři mezipaměti místní globální balíčky:

`dotnet nuget locals -c global-packages`

Vymaže všechny soubory v adresáři místní dočasné mezipaměti:

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Poradce při potížích

Informace o běžné problémy a chyby při použití `dotnet nuget locals` příkazů najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).