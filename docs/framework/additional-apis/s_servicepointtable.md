---
title: Třída ServicePointManager. s_ServicePointTable – pole
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120002"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Třída ServicePointManager. s\_pole ServicePointTable

`ServicePointManager.s_ServicePointTable` je <xref:System.Collections.Hashtable>, který obsahuje seznam aktivních připojení HTTP (<xref:System.Net.ServicePoint>s) v <xref:System.AppDomain>.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Pole `ServicePointManager.s_ServicePointTable` je soukromé a není určeno pro použití přímo v kódu.
> 
> Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Net>

**Sestavení:** Systém (v System. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
