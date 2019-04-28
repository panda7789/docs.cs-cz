---
title: ServicePointManager.s_ServicePointTable Field
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ebcf5c3f13b3bd30a8e091be09ae546eee1eaffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675439"
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="f79aa-102">ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="f79aa-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="f79aa-103">`ServicePointManager.s_ServicePointTable` je <xref:System.Collections.Hashtable> , který obsahuje seznam aktivních připojení HTTP (<xref:System.Net.ServicePoint>s) v <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="f79aa-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="f79aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f79aa-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="f79aa-105">`ServicePointManager.s_ServicePointTable` Pole je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f79aa-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="f79aa-106">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="f79aa-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f79aa-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f79aa-107">Requirements</span></span>

<span data-ttu-id="f79aa-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f79aa-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f79aa-109">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="f79aa-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f79aa-110">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="f79aa-110">**.NET Framework versions:** Available since 2.0.</span></span>
