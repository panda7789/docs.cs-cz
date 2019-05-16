---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632411"
---
# <a name="dotnet-list-reference"></a>referenční seznam DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet list reference` -Obsahuje seznam odkazů typu projekt na projekt.

## <a name="synopsis"></a>Souhrn

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Popis

`dotnet list reference` Příkaz poskytuje vhodnou možnost do odkazů projektu seznamu pro daný projekt nebo řešení.

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Určuje soubor projektu má použít pro zobrazení seznamu odkazů. Pokud není zadán, příkaz vyhledá v aktuálním adresáři souboru projektu.

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
