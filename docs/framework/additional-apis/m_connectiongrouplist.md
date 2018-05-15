---
title: ServicePoint.m_ConnectionGroupList pole
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 25caec18f7d2c51f03028b52c1a4957bb1cd2589
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="servicepointmconnectiongrouplist-field"></a><span data-ttu-id="7287f-102">ServicePoint.m\_ConnectionGroupList pole</span><span class="sxs-lookup"><span data-stu-id="7287f-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="7287f-103">`ServicePoint.m_ConnectionGroupList` je <xref:System.Collections.Hashtable> skupin připojení, každý podržíte připojení pro <xref:System.Net.ServicePoint>je identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="7287f-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="7287f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7287f-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="7287f-105">`ServicePoint.m_ConnectionGroupList` Pole je privátní a nejsou určeny pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="7287f-105">The `ServicePoint.m_ConnectionGroupList` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="7287f-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="7287f-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7287f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7287f-107">Requirements</span></span>

<span data-ttu-id="7287f-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7287f-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7287f-109">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="7287f-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="7287f-110">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="7287f-110">**.NET Framework versions:** Available since 2.0.</span></span>
