---
title: "IHostMalloc – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="917a8-102">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="917a8-102">IHostMalloc Interface</span></span>
<span data-ttu-id="917a8-103">Poskytuje metody, které povolit modul CLR (CLR) do požádat podrobných přidělení haldy prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="917a8-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="917a8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="917a8-104">Methods</span></span>  
  
|<span data-ttu-id="917a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="917a8-105">Method</span></span>|<span data-ttu-id="917a8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="917a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="917a8-107">ALLOC – metoda</span><span class="sxs-lookup"><span data-stu-id="917a8-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="917a8-108">Požadavky, že hostitel přidělit požadované množství paměti z haldě.</span><span class="sxs-lookup"><span data-stu-id="917a8-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="917a8-109">Debugalloc – metoda</span><span class="sxs-lookup"><span data-stu-id="917a8-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="917a8-110">Požadavky, přidělit požadované množství paměti z haldy hostitel a dále sledovat, kdy byl přidělen paměť.</span><span class="sxs-lookup"><span data-stu-id="917a8-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="917a8-111">Free – metoda</span><span class="sxs-lookup"><span data-stu-id="917a8-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="917a8-112">Uvolní paměť, která byla přidělena pomocí `Alloc` metoda.</span><span class="sxs-lookup"><span data-stu-id="917a8-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="917a8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="917a8-113">Remarks</span></span>  
 <span data-ttu-id="917a8-114">Modul CLR získá ukazatele rozhraní k `IHostMalloc` instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="917a8-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="917a8-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="917a8-115">Requirements</span></span>  
 <span data-ttu-id="917a8-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="917a8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="917a8-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="917a8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="917a8-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="917a8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="917a8-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="917a8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917a8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="917a8-120">See Also</span></span>  
 [<span data-ttu-id="917a8-121">Ihostmemorymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="917a8-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="917a8-122">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="917a8-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
