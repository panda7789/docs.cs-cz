---
title: "IMethodMalloc – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="71300-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71300-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="71300-103">Poskytuje metodu pro přidělení paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="71300-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71300-104">`IMethodMalloc` Rozhraní je přidělení jednoduché paměti.</span><span class="sxs-lookup"><span data-stu-id="71300-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="71300-105">Umožní vám přidělit paměť, ale nechcete ho volné.</span><span class="sxs-lookup"><span data-stu-id="71300-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71300-106">Metody</span><span class="sxs-lookup"><span data-stu-id="71300-106">Methods</span></span>  
  
|<span data-ttu-id="71300-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="71300-107">Method</span></span>|<span data-ttu-id="71300-108">Popis</span><span class="sxs-lookup"><span data-stu-id="71300-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71300-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="71300-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="71300-110">Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce MSIL.</span><span class="sxs-lookup"><span data-stu-id="71300-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71300-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71300-111">Remarks</span></span>  
 <span data-ttu-id="71300-112">Každý allocator je modulů a zajistí, že tělo funkce bude v kladné posun od základní modulu.</span><span class="sxs-lookup"><span data-stu-id="71300-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="71300-113">Paměť nad základní modulu může být drahocenný, takže přidělujícího modulu se má použít k přidělení paměti pouze pro tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="71300-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71300-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71300-114">Requirements</span></span>  
 <span data-ttu-id="71300-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71300-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71300-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71300-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71300-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71300-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71300-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71300-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71300-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="71300-119">See Also</span></span>  
 [<span data-ttu-id="71300-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="71300-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
