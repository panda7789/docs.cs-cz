---
title: příkaz DotNet odebrat odkaz
description: Příkaz dotnet odebrat odkaz poskytuje pohodlné možnost pro odebrání odkazů typu projekt na projekt.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170610"
---
# <a name="dotnet-remove-reference"></a>DotNet odebrat odkaz

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet remove reference` – Odebere odkazy typu projekt projekt.

## <a name="synopsis"></a>Souhrn

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Popis

`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.

## <a name="arguments"></a>Arguments

`PROJECT`

Cílový soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

`PROJECT_REFERENCES`

Chcete-li odebrat odkazuje na projekt na projekt (P2P). Můžete určit jeden nebo více projektů. [Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux na základě terminály.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-f|--framework <FRAMEWORK>`

Odebere odkaz pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).

## <a name="examples"></a>Příklady

Odebrání odkazu na projekt ze zadaného projektu:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Odeberte odkazy na více projektu z projektu v aktuálním adresáři:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Odeberte odkazy na více projektů pomocí vzoru pro glob v systému Unix/Linux:

`dotnet remove app/app.csproj reference **/*.csproj`
