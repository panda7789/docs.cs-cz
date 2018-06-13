---
title: IHostThreadPoolManager – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92097cdf735630f3537296f188bd83ea8162add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441126"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="df23e-102">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df23e-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="df23e-103">Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.</span><span class="sxs-lookup"><span data-stu-id="df23e-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df23e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="df23e-104">Methods</span></span>  
  
|<span data-ttu-id="df23e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-105">Method</span></span>|<span data-ttu-id="df23e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="df23e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df23e-107">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="df23e-108">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="df23e-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="df23e-109">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="df23e-110">Získá maximální počet vláken, která udržuje hostitele současně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="df23e-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="df23e-111">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="df23e-112">Získá minimální počet nečinných vláken, která udržuje hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="df23e-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="df23e-113">QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="df23e-114">Funkce pro spuštění front a poskytuje objekt obsahující data, která má být používána funkce.</span><span class="sxs-lookup"><span data-stu-id="df23e-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="df23e-115">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="df23e-116">Nastaví maximální počet vláken, které hostitele může udržují ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="df23e-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="df23e-117">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="df23e-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="df23e-118">Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="df23e-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df23e-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df23e-119">Remarks</span></span>  
 <span data-ttu-id="df23e-120">Hostitel není potřeba konfigurovat fond vláken pomocí hodnoty zadané ve volání `SetMaxThreads` a `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="df23e-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="df23e-121">V takovém případě by měl vrátit hostitele má hodnotu HRESULT E_NOTIMPL z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="df23e-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df23e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df23e-122">Requirements</span></span>  
 <span data-ttu-id="df23e-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df23e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df23e-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df23e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df23e-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df23e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df23e-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df23e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df23e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="df23e-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="df23e-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="df23e-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
