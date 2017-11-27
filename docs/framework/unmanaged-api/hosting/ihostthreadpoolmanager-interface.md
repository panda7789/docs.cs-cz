---
title: "IHostThreadPoolManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2773042c695320ab1e90d4c5d341e2df5f0f778f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="1e34e-102">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e34e-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="1e34e-103">Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.</span><span class="sxs-lookup"><span data-stu-id="1e34e-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e34e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1e34e-104">Methods</span></span>  
  
|<span data-ttu-id="1e34e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-105">Method</span></span>|<span data-ttu-id="1e34e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1e34e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e34e-107">Getavailablethreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="1e34e-108">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="1e34e-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="1e34e-109">Getmaxthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="1e34e-110">Získá maximální počet vláken, která udržuje hostitele současně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="1e34e-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="1e34e-111">Getminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="1e34e-112">Získá minimální počet nečinných vláken, která udržuje hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="1e34e-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="1e34e-113">QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="1e34e-114">Funkce pro spuštění front a poskytuje objekt obsahující data, která má být používána funkce.</span><span class="sxs-lookup"><span data-stu-id="1e34e-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="1e34e-115">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="1e34e-116">Nastaví maximální počet vláken, které hostitele může udržují ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="1e34e-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="1e34e-117">Setminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="1e34e-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="1e34e-118">Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="1e34e-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e34e-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e34e-119">Remarks</span></span>  
 <span data-ttu-id="1e34e-120">Hostitel není potřeba konfigurovat fond vláken pomocí hodnoty zadané ve volání `SetMaxThreads` a `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="1e34e-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="1e34e-121">V takovém případě by měl vrátit hostitele má hodnotu HRESULT E_NOTIMPL z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="1e34e-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e34e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e34e-122">Requirements</span></span>  
 <span data-ttu-id="1e34e-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e34e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e34e-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e34e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e34e-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e34e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e34e-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e34e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e34e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e34e-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="1e34e-128">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="1e34e-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
