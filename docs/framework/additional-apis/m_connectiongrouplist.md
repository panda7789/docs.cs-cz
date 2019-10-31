---
title: ServicePoint. m_ConnectionGroupList – pole
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1991dae4d03f617857b860f920077531f7937bf1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120050"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="03e85-102">ServicePoint. m\_pole ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="03e85-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="03e85-103">`ServicePoint.m_ConnectionGroupList` je <xref:System.Collections.Hashtable> skupin připojení, každé drží připojení k identifikátoru URI <xref:System.Net.ServicePoint>.</span><span class="sxs-lookup"><span data-stu-id="03e85-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="03e85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03e85-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="03e85-105">Pole `ServicePoint.m_ConnectionGroupList` je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="03e85-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="03e85-106">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="03e85-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="03e85-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03e85-107">Requirements</span></span>

<span data-ttu-id="03e85-108">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="03e85-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="03e85-109">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="03e85-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="03e85-110">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="03e85-110">**.NET Framework versions:** Available since 2.0.</span></span>
