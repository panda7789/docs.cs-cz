---
title: Pole ServicePoint.m_ConnectionGroupList
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
ms.openlocfilehash: 2b1b46085ed035b67fd01447727b406fe3895980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155892"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="23a65-102">Pole ServicePoint.m\_ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="23a65-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="23a65-103">`ServicePoint.m_ConnectionGroupList`je <xref:System.Collections.Hashtable> skupinou připojení, z nichž <xref:System.Net.ServicePoint>každá drží připojení identifikátoru URI programu .</span><span class="sxs-lookup"><span data-stu-id="23a65-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="23a65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a65-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="23a65-105">Pole `ServicePoint.m_ConnectionGroupList` je soukromé a není určeno k použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="23a65-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="23a65-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="23a65-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="23a65-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23a65-107">Requirements</span></span>

<span data-ttu-id="23a65-108">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="23a65-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="23a65-109">**Sestava:** Systém (v souboru System.dll)</span><span class="sxs-lookup"><span data-stu-id="23a65-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="23a65-110">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="23a65-110">**.NET Framework versions:** Available since 2.0.</span></span>
