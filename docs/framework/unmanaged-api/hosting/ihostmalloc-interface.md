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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136406"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="19e89-102">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19e89-102">IHostMalloc Interface</span></span>
<span data-ttu-id="19e89-103">Poskytuje metody, které umožňují common language runtime (CLR) pro žádosti o jemně odstupňovaných přidělení haldy přes hostitele.</span><span class="sxs-lookup"><span data-stu-id="19e89-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19e89-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19e89-104">Methods</span></span>  
  
|<span data-ttu-id="19e89-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19e89-105">Method</span></span>|<span data-ttu-id="19e89-106">Popis</span><span class="sxs-lookup"><span data-stu-id="19e89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19e89-107">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="19e89-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="19e89-108">Požadavky, že hostitel přidělit požadované množství paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="19e89-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="19e89-109">DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="19e89-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="19e89-110">Požadavky, přidělit požadované množství paměti z haldy hostitele a také sledovat, kde byla přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="19e89-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="19e89-111">Free – metoda</span><span class="sxs-lookup"><span data-stu-id="19e89-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="19e89-112">Uvolnění paměti, která byla přidělena pomocí `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="19e89-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19e89-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19e89-113">Remarks</span></span>  
 <span data-ttu-id="19e89-114">Modul CLR načte ukazatel rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="19e89-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19e89-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19e89-115">Requirements</span></span>  
 <span data-ttu-id="19e89-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19e89-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19e89-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19e89-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19e89-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19e89-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19e89-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19e89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e89-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19e89-120">See also</span></span>

- [<span data-ttu-id="19e89-121">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19e89-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="19e89-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="19e89-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
