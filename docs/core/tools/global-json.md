---
title: odkaz na Global.JSON
description: Najdete v části schéma pro global.json souboru, který umožňuje nastavení verze nástrojů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209967"
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
