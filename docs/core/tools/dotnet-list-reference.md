---
title: dotnet – příkaz odkazu na seznam
description: Příkaz referenčního seznamu dotnet nabízí pohodlný možnost seznamu odkazů na projekt.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802755"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí

## <a name="name"></a>Name

`dotnet list reference`-Obsahuje odkazy z projektu na projekt.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a>Popis

`dotnet list reference`Příkaz nabízí pohodlný možnost zobrazit odkazy projektu pro daný projekt.

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Soubor projektu, na kterém má být provozován. Pokud soubor není zadán, příkaz bude hledat v aktuálním adresáři.

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

* Vypíše odkazy projektu pro zadaný projekt:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Vypíše odkazy na projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet list reference
  ```
