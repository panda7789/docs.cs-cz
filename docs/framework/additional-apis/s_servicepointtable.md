---
title: Třída ServicePointManager. s_ServicePointTable – pole
description: Přečtěte si o poli Třída ServicePointManager. s_ServicePointTable v .NET. Toto pole zatřiďovací tabulky obsahuje aktivní připojení HTTP (ServicePoints) v doméně AppDomain.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989543"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Třída ServicePointManager. s \_ ServicePointTable – pole

`ServicePointManager.s_ServicePointTable`je a <xref:System.Collections.Hashtable> , který obsahuje seznam aktivních připojení http <xref:System.Net.ServicePoint> v <xref:System.AppDomain> .

## <a name="syntax"></a>Syntax
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`Pole je soukromé a není určeno pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
