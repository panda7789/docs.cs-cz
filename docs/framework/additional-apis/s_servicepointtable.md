---
title: Třída ServicePointManager. s_ServicePointTable – pole
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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214923"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="9f646-102">Třída ServicePointManager. s\_pole ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="9f646-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="9f646-103">`ServicePointManager.s_ServicePointTable` je <xref:System.Collections.Hashtable>, který obsahuje seznam aktivních připojení HTTP (<xref:System.Net.ServicePoint>s) v <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9f646-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f646-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f646-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="9f646-105">Pole `ServicePointManager.s_ServicePointTable` je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9f646-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="9f646-106">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9f646-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f646-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f646-107">Requirements</span></span>

<span data-ttu-id="9f646-108">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9f646-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9f646-109">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="9f646-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9f646-110">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="9f646-110">**.NET Framework versions:** Available since 2.0.</span></span>
