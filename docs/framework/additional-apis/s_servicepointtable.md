---
title: Pole ServicePointManager.s_ServicePointTable
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155808"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="3a234-102">Pole ServicePointManager.s\_ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="3a234-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="3a234-103">`ServicePointManager.s_ServicePointTable`je <xref:System.Collections.Hashtable> a, který obsahuje seznam<xref:System.Net.ServicePoint>aktivních připojení <xref:System.AppDomain>HTTP ( s) v .</span><span class="sxs-lookup"><span data-stu-id="3a234-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a234-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="3a234-105">Pole `ServicePointManager.s_ServicePointTable` je soukromé a není určeno k použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="3a234-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="3a234-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="3a234-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a234-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a234-107">Requirements</span></span>

<span data-ttu-id="3a234-108">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="3a234-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="3a234-109">**Sestava:** Systém (v souboru System.dll)</span><span class="sxs-lookup"><span data-stu-id="3a234-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="3a234-110">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="3a234-110">**.NET Framework versions:** Available since 2.0.</span></span>
