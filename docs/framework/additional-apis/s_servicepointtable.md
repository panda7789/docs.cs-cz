---
title: ServicePointManager.s_ServicePointTable pole
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable pole

`ServicePointManager.s_ServicePointTable`je <xref:System.Collections.Hashtable> obsahující seznam aktivních připojení protokolu HTTP (<xref:System.Net.ServicePoint>s) v <xref:System.AppDomain>.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable` Pole je privátní a nejsou určeny pro použití přímo v kódu.
> 
> Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:**<xref:System.Net>

**Sestavení:** systému (v System.dll)

**Verze rozhraní .NET framework:** dostupné od verze 2.0.
