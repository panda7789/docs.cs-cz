---
title: "DotNet odebrat balíček příkaz - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet odebrat balíček poskytuje vhodnou možnost odebrat odkaz na balíček NuGet do projektu."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a>Odebrat balíček DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet remove package`– Odebere odkaz na balíček ze souboru projektu.

## <a name="synopsis"></a>Stručný obsah

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Popis

`dotnet remove package` Příkaz poskytuje vhodnou možnost odebrat odkaz balíčku NuGet z projektu.

## <a name="arguments"></a>Arguments

`PROJECT`

Určuje soubor projektu. Pokud není zadáno, bude příkaz hledání aktuální adresář pro jednu.

`PACKAGE_NAME`

Odkaz na balíček odebrat.

## <a name="options"></a>Možnosti

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

## <a name="examples"></a>Příklady

Odebere `Newtonsoft.Json` balíček NuGet z projektu v aktuálním adresáři:

`dotnet remove package Newtonsoft.Json`
