---
title: odkaz na Global.JSON
description: "Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
