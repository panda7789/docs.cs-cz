---
title: příkaz odkaz DotNet seznamu - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet seznamu odkaz poskytuje vhodnou možnost do seznamu odkazy na projekt na projekt.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a>referenční seznam DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet list reference` -Obsahuje seznam odkazů projektu do projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Popis

`dotnet list reference` Příkaz poskytuje vhodnou možnost do seznamu odkazy na projekt pro daný projekt.

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu pro výpis odkazy. Pokud není zadáno, bude příkaz Hledat aktuální adresář pro soubor projektu.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Seznam odkazy na projekt pro zadaného projektu:

`dotnet list app/app.csproj reference`

Seznam odkazů projektu pro projekt v aktuálním adresáři:

`dotnet list reference`
