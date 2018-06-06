---
title: příkaz odkaz DotNet seznamu - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet seznamu odkaz poskytuje vhodnou možnost do seznamu odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 821e6d276af44bf984c8ac1b42b4e954dbe69556
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697180"
---
# <a name="dotnet-list-reference"></a>referenční seznam DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet list reference` -Obsahuje seznam odkazů projektu projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Popis

`dotnet list reference` Příkaz poskytuje vhodnou možnost do seznamu odkazy na projekt pro daný projekt.

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu pro výpis odkazy. Pokud není zadaný, hledá příkaz aktuální adresář pro soubor projektu.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Seznam odkazy na projekt pro zadaného projektu:

`dotnet list app/app.csproj reference`

Seznam odkazů projektu pro projekt v aktuálním adresáři:

`dotnet list reference`