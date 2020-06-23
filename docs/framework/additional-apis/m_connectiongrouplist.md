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
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="b899f-103">ServicePoint. m \_ ConnectionGroupList – pole</span><span class="sxs-lookup"><span data-stu-id="b899f-103">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="b899f-104">`ServicePoint.m_ConnectionGroupList`je <xref:System.Collections.Hashtable> Skupina připojení, každá drží připojení pro <xref:System.Net.ServicePoint> identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="b899f-104">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="b899f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b899f-105">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="b899f-106">`ServicePoint.m_ConnectionGroupList`Pole je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="b899f-106">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b899f-107">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b899f-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b899f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b899f-108">Requirements</span></span>

<span data-ttu-id="b899f-109">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b899f-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b899f-110">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="b899f-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b899f-111">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="b899f-111">**.NET Framework versions:** Available since 2.0.</span></span>
