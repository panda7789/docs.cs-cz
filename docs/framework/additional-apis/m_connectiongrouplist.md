---
title: ServicePoint.m_ConnectionGroupList Field
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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 85359492fbf06942a57c51142620cab015999b31
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300867"
---
# <a name="servicepointmconnectiongrouplist-field"></a><span data-ttu-id="556c3-102">ServicePoint.m\_ConnectionGroupList pole</span><span class="sxs-lookup"><span data-stu-id="556c3-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="556c3-103">`ServicePoint.m_ConnectionGroupList` je <xref:System.Collections.Hashtable> skupin připojení jednotlivých uchovávající připojení <xref:System.Net.ServicePoint>na identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="556c3-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="556c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="556c3-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="556c3-105">`ServicePoint.m_ConnectionGroupList` Pole je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="556c3-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="556c3-106">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="556c3-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="556c3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="556c3-107">Requirements</span></span>

<span data-ttu-id="556c3-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="556c3-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="556c3-109">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="556c3-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="556c3-110">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="556c3-110">**.NET Framework versions:** Available since 2.0.</span></span>
