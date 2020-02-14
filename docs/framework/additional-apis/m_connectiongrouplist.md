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
ms.openlocfilehash: f2759f82f335415edf7bab33edbd446eec6ffbb5
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215522"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="c9278-102">ServicePoint. m\_pole ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="c9278-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="c9278-103">`ServicePoint.m_ConnectionGroupList` je <xref:System.Collections.Hashtable> skupin připojení, každé drží připojení k identifikátoru URI <xref:System.Net.ServicePoint>.</span><span class="sxs-lookup"><span data-stu-id="c9278-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9278-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9278-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="c9278-105">Pole `ServicePoint.m_ConnectionGroupList` je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="c9278-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="c9278-106">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9278-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9278-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9278-107">Requirements</span></span>

<span data-ttu-id="c9278-108">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c9278-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c9278-109">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="c9278-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c9278-110">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="c9278-110">**.NET Framework versions:** Available since 2.0.</span></span>
