---
title: IHostMalloc – rozhraní
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804606"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="91416-102">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91416-102">IHostMalloc Interface</span></span>
<span data-ttu-id="91416-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vyžadovat jemně odstupňované přidělení z haldy prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="91416-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91416-104">Metody</span><span class="sxs-lookup"><span data-stu-id="91416-104">Methods</span></span>  
  
|<span data-ttu-id="91416-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="91416-105">Method</span></span>|<span data-ttu-id="91416-106">Popis</span><span class="sxs-lookup"><span data-stu-id="91416-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91416-107">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="91416-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="91416-108">Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="91416-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="91416-109">DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="91416-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="91416-110">Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.</span><span class="sxs-lookup"><span data-stu-id="91416-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="91416-111">Free – metoda</span><span class="sxs-lookup"><span data-stu-id="91416-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="91416-112">Uvolňuje paměť, která byla přidělena pomocí `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="91416-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91416-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91416-113">Remarks</span></span>  
 <span data-ttu-id="91416-114">CLR získá ukazatel rozhraní na `IHostMalloc` instanci voláním metody [IHostMemoryManager:: CreateMalloc –](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91416-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91416-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91416-115">Requirements</span></span>  
 <span data-ttu-id="91416-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91416-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91416-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91416-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91416-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91416-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91416-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91416-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91416-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="91416-120">See also</span></span>

- [<span data-ttu-id="91416-121">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91416-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="91416-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="91416-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
