---
title: Třída ServicePointManager. s_ServicePointTable – pole
description: Přečtěte si o poli Třída ServicePointManager. s_ServicePointTable v .NET. Toto pole zatřiďovací tabulky obsahuje aktivní připojení HTTP (ServicePoints) v doméně AppDomain.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989543"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="cdd49-104">Třída ServicePointManager. s \_ ServicePointTable – pole</span><span class="sxs-lookup"><span data-stu-id="cdd49-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="cdd49-105">`ServicePointManager.s_ServicePointTable`je a <xref:System.Collections.Hashtable> , který obsahuje seznam aktivních připojení http <xref:System.Net.ServicePoint> v <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="cdd49-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdd49-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdd49-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="cdd49-107">`ServicePointManager.s_ServicePointTable`Pole je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="cdd49-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cdd49-108">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cdd49-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdd49-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdd49-109">Requirements</span></span>

<span data-ttu-id="cdd49-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="cdd49-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="cdd49-111">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="cdd49-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="cdd49-112">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="cdd49-112">**.NET Framework versions:** Available since 2.0.</span></span>
