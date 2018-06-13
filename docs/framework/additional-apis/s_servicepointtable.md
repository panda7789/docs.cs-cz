---
title: ServicePointManager.s_ServicePointTable pole
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5450a0cb3e5bd39a86365b16d372c7e573a43496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351755"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable pole

`ServicePointManager.s_ServicePointTable` je <xref:System.Collections.Hashtable> obsahující seznam aktivních připojení protokolu HTTP (<xref:System.Net.ServicePoint>s) v <xref:System.AppDomain>.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Pole je privátní a nejsou určeny pro použití přímo v kódu.
> 
> Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Net>

**Sestavení:** systému (v System.dll)

**Verze rozhraní .NET framework:** dostupné od verze 2.0.
