---
title: odkaz na Global.JSON
description: Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a>odkaz na Global.JSON

*Global.json* souboru umožňuje výběr verze nástrojů .NET Core používá prostřednictvím `sdk` vlastnost.

Nástrojů příkazového řádku .NET core vyhledejte tento soubor v aktuálním pracovním adresáři (který není nutně stejná jako adresáři projektu) nebo jednoho z jeho nadřazené adresáře.

## <a name="sdk"></a>Sada SDK
Typ: objekt

Určuje informace o sadě SDK.

### <a name="version"></a>verze
Typ: řetězec

Verze sady SDK k použití.

Příklad:

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
