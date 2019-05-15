---
title: Odebrat balíček příkaz DotNet
description: Příkaz dotnet odebrat balíček poskytuje pohodlné možnost pro odebrání odkazu na balíček NuGet do projektu.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632438"
---
# <a name="dotnet-remove-package"></a>DotNet odebrat balíček

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet remove package` – Odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Souhrn

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Popis

`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat z projektu odkaz na balíček NuGet.

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

`PACKAGE_NAME`

Odkaz na balíček k odebrání.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:

`dotnet remove package Newtonsoft.Json`
