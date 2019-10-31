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
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136781"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="c517e-102">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c517e-102">IHostMalloc Interface</span></span>
<span data-ttu-id="c517e-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vyžadovat jemně odstupňované přidělení z haldy prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="c517e-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c517e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c517e-104">Methods</span></span>  
  
|<span data-ttu-id="c517e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c517e-105">Method</span></span>|<span data-ttu-id="c517e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c517e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c517e-107">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="c517e-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="c517e-108">Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="c517e-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="c517e-109">DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="c517e-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="c517e-110">Požaduje, aby hostitel přidělil požadovanou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.</span><span class="sxs-lookup"><span data-stu-id="c517e-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="c517e-111">Free – metoda</span><span class="sxs-lookup"><span data-stu-id="c517e-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="c517e-112">Uvolní paměť, která byla přidělena pomocí metody `Alloc`.</span><span class="sxs-lookup"><span data-stu-id="c517e-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c517e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c517e-113">Remarks</span></span>  
 <span data-ttu-id="c517e-114">Modul CLR získá ukazatel rozhraní na instanci `IHostMalloc` voláním metody [IHostMemoryManager:: CreateMalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c517e-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c517e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c517e-115">Requirements</span></span>  
 <span data-ttu-id="c517e-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c517e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c517e-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c517e-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c517e-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c517e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c517e-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c517e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c517e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c517e-120">See also</span></span>

- [<span data-ttu-id="c517e-121">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c517e-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="c517e-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c517e-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
