---
title: příkaz DotNet seznamu odkaz
description: Příkaz dotnet seznamu odkaz nabízí pohodlný parametr pro seznam odkazů typu projekt na projekt.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169830"
---
# <a name="dotnet-list-reference"></a>referenční seznam DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

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