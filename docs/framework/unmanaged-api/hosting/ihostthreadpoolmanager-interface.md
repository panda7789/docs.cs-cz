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
ms.openlocfilehash: bac29b5950f1547c5c60ac716d40d2ef4b1a2cc2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842477"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="43848-102">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43848-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="43848-103">Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) nakonfiguroval fond vláken a zařadil pracovní položky do fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="43848-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43848-104">Metody</span><span class="sxs-lookup"><span data-stu-id="43848-104">Methods</span></span>  
  
|<span data-ttu-id="43848-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="43848-105">Method</span></span>|<span data-ttu-id="43848-106">Popis</span><span class="sxs-lookup"><span data-stu-id="43848-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43848-107">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-107">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="43848-108">Získá počet vláken ve fondu vláken, které aktuálně nezpracovávají pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="43848-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="43848-109">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-109">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="43848-110">Získá maximální počet vláken, která hostitel udržuje souběžně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="43848-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="43848-111">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-111">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="43848-112">Získá minimální počet nečinných vláken, která hostitel udržuje při předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="43848-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="43848-113">QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-113">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="43848-114">Zařadí funkci do fronty pro spuštění a poskytuje objekt obsahující data, která má funkce používat.</span><span class="sxs-lookup"><span data-stu-id="43848-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="43848-115">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-115">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="43848-116">Nastaví maximální počet vláken, která může hostitel udržovat ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="43848-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="43848-117">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="43848-117">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="43848-118">Nastaví minimální počet nečinných vláken, které musí hostitel uchovávat při předvídání požadavků.</span><span class="sxs-lookup"><span data-stu-id="43848-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43848-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43848-119">Remarks</span></span>  
 <span data-ttu-id="43848-120">Hostitel není vyžadován ke konfiguraci fondu vláken pomocí hodnot zadaných v volání `SetMaxThreads` `SetMinThreads` metod a.</span><span class="sxs-lookup"><span data-stu-id="43848-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="43848-121">V takovém případě by hostitel měl z těchto metod vrátit hodnotu HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="43848-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43848-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43848-122">Requirements</span></span>  
 <span data-ttu-id="43848-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43848-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43848-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43848-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43848-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43848-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43848-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43848-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43848-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="43848-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="43848-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="43848-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
