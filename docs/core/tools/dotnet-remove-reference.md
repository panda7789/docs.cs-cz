---
title: příkaz odkaz DotNet remove - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet odebrat odkaz poskytuje vhodnou možnost odebrat odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 209f1ad62221e8a80efa161354a2c074d74b7c5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-remove-reference"></a>Odebrat odkaz DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet remove reference` – Odebere odkazy na projekt na projekt.

## <a name="synopsis"></a>Stručný obsah

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>Popis

`dotnet remove reference` Příkaz poskytuje vhodnou možnost odebrat odkazy na projekt z projektu.

## <a name="arguments"></a>Arguments

`PROJECT`

Cílový soubor projektu. Pokud není zadaný, hledá příkaz aktuální adresář pro jednu.

`PROJECT_REFERENCES`

Projekt do projektu (P2P odkazy na odebrat. Můžete určit jeden nebo více projektů. [Vzory glob](https://en.wikipedia.org/wiki/Glob_(programming)) jsou podporovány v systému Unix/Linux, na základě terminály.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-f|--framework <FRAMEWORK>`

Odebere odkaz jenom při cílení na konkrétní [framework](../../standard/frameworks.md).

## <a name="examples"></a>Příklady

Odeberte odkaz na projekt z zadaného projektu:

`dotnet remove app/app.csproj reference lib/lib.csproj`

Odebrání více odkazy na projekt na projekt v aktuálním adresáři:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Odebrání více odkazů projektu pomocí vzoru glob na systému Unix/Linux:

`dotnet remove app/app.csproj reference **/*.csproj`
