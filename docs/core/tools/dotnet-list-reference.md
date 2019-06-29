---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421833"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet list reference` -Obsahuje seznam odkazů typu projekt na projekt.

## <a name="synopsis"></a>Souhrn

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Popis

`dotnet list reference` Příkaz poskytuje vhodnou možnost do odkazů projektu seznamu pro daný projekt nebo řešení.

## <a name="arguments"></a>Arguments

* **`PROJECT | SOLUTION`**

  Určuje soubor projektu nebo řešení má použít pro zobrazení seznamu odkazů. Pokud není zadán, příkaz vyhledá v aktuálním adresáři souboru projektu.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

## <a name="examples"></a>Příklady

* Vypište odkazy na projekt pro zadaný projekt:

  ```console
  dotnet list app/app.csproj reference
  ```

* Seznam odkazů projektu pro projekt v aktuálním adresáři:

  ```console
  dotnet list reference
  ```
