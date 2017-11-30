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
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
