---
title: ServicePoint. m_ConnectionGroupList – pole
description: Seznamte se s ServicePoint. m_ConnectionGroupList a zatřiďovací tabulkou skupin připojení, které každý z nich drží připojení pro identifikátor URI ServicePoint v .NET.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989716"
---
# <a name="servicepointm_connectiongrouplist-field"></a>ServicePoint. m \_ ConnectionGroupList – pole

`ServicePoint.m_ConnectionGroupList`je <xref:System.Collections.Hashtable> Skupina připojení, každá drží připojení pro <xref:System.Net.ServicePoint> identifikátor URI.

## <a name="syntax"></a>Syntax
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> `ServicePoint.m_ConnectionGroupList`Pole je soukromé a není určeno pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
