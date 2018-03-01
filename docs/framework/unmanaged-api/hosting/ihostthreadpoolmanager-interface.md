---
title: "IHostThreadPoolManager – rozhraní"
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
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd58c53deec0a895ae6f67cccf26d2c8c2530be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="b5e1d-102">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5e1d-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="b5e1d-103">Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5e1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b5e1d-104">Methods</span></span>  
  
|<span data-ttu-id="b5e1d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-105">Method</span></span>|<span data-ttu-id="b5e1d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b5e1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5e1d-107">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="b5e1d-108">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="b5e1d-109">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="b5e1d-110">Získá maximální počet vláken, která udržuje hostitele současně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="b5e1d-111">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="b5e1d-112">Získá minimální počet nečinných vláken, která udržuje hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="b5e1d-113">QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="b5e1d-114">Funkce pro spuštění front a poskytuje objekt obsahující data, která má být používána funkce.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="b5e1d-115">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="b5e1d-116">Nastaví maximální počet vláken, které hostitele může udržují ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="b5e1d-117">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b5e1d-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="b5e1d-118">Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e1d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5e1d-119">Remarks</span></span>  
 <span data-ttu-id="b5e1d-120">Hostitel není potřeba konfigurovat fond vláken pomocí hodnoty zadané ve volání `SetMaxThreads` a `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="b5e1d-121">V takovém případě by měl vrátit hostitele má hodnotu HRESULT E_NOTIMPL z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="b5e1d-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e1d-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5e1d-122">Requirements</span></span>  
 <span data-ttu-id="b5e1d-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e1d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e1d-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5e1d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5e1d-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5e1d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5e1d-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e1d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e1d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5e1d-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="b5e1d-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b5e1d-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
