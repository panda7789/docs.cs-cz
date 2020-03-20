---
title: Pole ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155808"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Pole ServicePointManager.s\_ServicePointTable

`ServicePointManager.s_ServicePointTable`je <xref:System.Collections.Hashtable> a, který obsahuje seznam<xref:System.Net.ServicePoint>aktivních připojení <xref:System.AppDomain>HTTP ( s) v .

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Pole `ServicePointManager.s_ServicePointTable` je soukromé a není určeno k použití přímo ve vašem kódu.
>
> Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikaci za žádných okolností.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestava:** Systém (v souboru System.dll)

**Verze rozhraní .NET Framework:** K dispozici od 2.0.
