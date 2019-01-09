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
ms.openlocfilehash: a764c74dc0927094675b0f5e0916a4ad29f04250
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151160"
---
# <a name="servicepointmconnectiongrouplist-field"></a><span data-ttu-id="be125-102">ServicePoint.m\_ConnectionGroupList pole</span><span class="sxs-lookup"><span data-stu-id="be125-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="be125-103">`ServicePoint.m_ConnectionGroupList` je <xref:System.Collections.Hashtable> skupin připojení jednotlivých uchovávající připojení <xref:System.Net.ServicePoint>na identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="be125-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="be125-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be125-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="be125-105">`ServicePoint.m_ConnectionGroupList` Pole je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="be125-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="be125-106">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="be125-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="be125-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be125-107">Requirements</span></span>

<span data-ttu-id="be125-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="be125-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="be125-109">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="be125-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="be125-110">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="be125-110">**.NET Framework versions:** Available since 2.0.</span></span>
