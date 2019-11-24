---
title: IMethodMalloc – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 3f840154d472dbcea7dfef7ba93e38c80b836734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447558"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="2254f-102">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2254f-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="2254f-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span><span class="sxs-lookup"><span data-stu-id="2254f-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2254f-104">The `IMethodMalloc` interface is a simple memory allocator.</span><span class="sxs-lookup"><span data-stu-id="2254f-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="2254f-105">It allows you to allocate memory, but not to free it.</span><span class="sxs-lookup"><span data-stu-id="2254f-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2254f-106">Metody</span><span class="sxs-lookup"><span data-stu-id="2254f-106">Methods</span></span>  
  
|<span data-ttu-id="2254f-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="2254f-107">Method</span></span>|<span data-ttu-id="2254f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2254f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2254f-109">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="2254f-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="2254f-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span><span class="sxs-lookup"><span data-stu-id="2254f-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2254f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2254f-111">Remarks</span></span>  
 <span data-ttu-id="2254f-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span><span class="sxs-lookup"><span data-stu-id="2254f-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="2254f-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span><span class="sxs-lookup"><span data-stu-id="2254f-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2254f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2254f-114">Requirements</span></span>  
 <span data-ttu-id="2254f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2254f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2254f-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2254f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2254f-117">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2254f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2254f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2254f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2254f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2254f-119">See also</span></span>

- [<span data-ttu-id="2254f-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2254f-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
