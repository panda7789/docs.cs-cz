---
title: příkaz DotNet odebrat odkaz
description: Příkaz dotnet odebrat odkaz poskytuje pohodlné možnost pro odebrání odkazů typu projekt na projekt.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648591"
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
