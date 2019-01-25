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
ms.openlocfilehash: ea3656fa00e84291ff7b2bdb65f9300cd7933c0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571779"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="ee45d-102">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee45d-102">IHostMalloc Interface</span></span>
<span data-ttu-id="ee45d-103">Poskytuje metody, které umožňují common language runtime (CLR) pro žádosti o jemně odstupňovaných přidělení haldy přes hostitele.</span><span class="sxs-lookup"><span data-stu-id="ee45d-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee45d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee45d-104">Methods</span></span>  
  
|<span data-ttu-id="ee45d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee45d-105">Method</span></span>|<span data-ttu-id="ee45d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ee45d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee45d-107">Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="ee45d-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="ee45d-108">Požadavky, že hostitel přidělit požadované množství paměti z haldy.</span><span class="sxs-lookup"><span data-stu-id="ee45d-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="ee45d-109">DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="ee45d-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="ee45d-110">Požadavky, přidělit požadované množství paměti z haldy hostitele a také sledovat, kde byla přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="ee45d-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="ee45d-111">Free – metoda</span><span class="sxs-lookup"><span data-stu-id="ee45d-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="ee45d-112">Uvolnění paměti, která byla přidělena pomocí `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="ee45d-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee45d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee45d-113">Remarks</span></span>  
 <span data-ttu-id="ee45d-114">Modul CLR načte ukazatel rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ee45d-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee45d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee45d-115">Requirements</span></span>  
 <span data-ttu-id="ee45d-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee45d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee45d-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee45d-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee45d-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee45d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee45d-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee45d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee45d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee45d-120">See also</span></span>
- [<span data-ttu-id="ee45d-121">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee45d-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="ee45d-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ee45d-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
