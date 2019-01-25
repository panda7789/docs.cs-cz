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
ms.openlocfilehash: b7fc0a271a9c62406d2942f387a5458e21211116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522723"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="a79ee-102">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a79ee-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="a79ee-103">Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a zařadit do fronty pracovních položek s fondem vláken.</span><span class="sxs-lookup"><span data-stu-id="a79ee-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a79ee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a79ee-104">Methods</span></span>  
  
|<span data-ttu-id="a79ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-105">Method</span></span>|<span data-ttu-id="a79ee-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a79ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a79ee-107">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="a79ee-108">Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="a79ee-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="a79ee-109">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="a79ee-110">Získá maximální počet vláken, která udržuje hostiteli současně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="a79ee-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="a79ee-111">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="a79ee-112">Získá minimální počet nečinných vláken, které udržuje hostitele čekat na případná požadavků.</span><span class="sxs-lookup"><span data-stu-id="a79ee-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="a79ee-113">QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="a79ee-114">Zařadí do fronty pro spuštění funkce a obsahuje objekt, který obsahuje data pro funkce.</span><span class="sxs-lookup"><span data-stu-id="a79ee-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="a79ee-115">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="a79ee-116">Nastaví maximální počet vláken, které hostitele může udržovat ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="a79ee-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="a79ee-117">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="a79ee-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="a79ee-118">Nastaví minimální počet nečinných vláken, které hostitele, musíte mít v předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="a79ee-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a79ee-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a79ee-119">Remarks</span></span>  
 <span data-ttu-id="a79ee-120">Hostitel není vyžadován konfigurace s použitím hodnoty zadané ve volání do fondu vláken `SetMaxThreads` a `SetMinThreads` metody.</span><span class="sxs-lookup"><span data-stu-id="a79ee-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="a79ee-121">V takovém případě hostitele by měl vrátit hodnotu HRESULT E_NOTIMPL z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="a79ee-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a79ee-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a79ee-122">Requirements</span></span>  
 <span data-ttu-id="a79ee-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a79ee-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a79ee-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a79ee-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a79ee-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a79ee-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a79ee-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a79ee-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79ee-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79ee-127">See also</span></span>
- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a79ee-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a79ee-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
