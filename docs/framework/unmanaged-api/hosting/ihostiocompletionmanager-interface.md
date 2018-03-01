---
title: "IHostIoCompletionManager – rozhraní"
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
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cbb4b87b57d4f5e11a9dab04d20dfb73170bb4a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="eb116-102">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb116-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="eb116-103">Poskytuje metody, které povolit modul CLR (CLR) pro interakci s porty dokončení vstupně-výstupních operací od hostitele.</span><span class="sxs-lookup"><span data-stu-id="eb116-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb116-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb116-104">Methods</span></span>  
  
|<span data-ttu-id="eb116-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-105">Method</span></span>|<span data-ttu-id="eb116-106">Popis</span><span class="sxs-lookup"><span data-stu-id="eb116-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb116-107">Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="eb116-108">Vytvoří vazbu k portu dokončení vstupně-výstupních operací popisovač.</span><span class="sxs-lookup"><span data-stu-id="eb116-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="eb116-109">CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="eb116-110">Zavření portů, která byla vytvořena pomocí dřívější volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="eb116-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="eb116-111">CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="eb116-112">Počet požadavků, hostitele vytvořit nový port dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="eb116-113">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="eb116-114">Získá počet vláken dokončení vstupně-výstupních operací, které nejsou aktuálně zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="eb116-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="eb116-115">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="eb116-116">Získá velikost vlastní data, která hostitele chtít připojit k vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="eb116-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="eb116-117">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="eb116-118">Získá maximální počet vláken, které můžete přidělit hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="eb116-119">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="eb116-120">Získá minimální počet vláken, která poskytuje hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="eb116-121">InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="eb116-122">Poskytuje hostitele příležitost k inicializaci vlastních dat o požadavek vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="eb116-123">SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="eb116-124">Poskytuje ukazatele rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="eb116-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="eb116-125">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="eb116-126">Nastaví maximální počet vláken, která allots hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="eb116-127">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="eb116-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="eb116-128">Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="eb116-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb116-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb116-129">Remarks</span></span>  
 <span data-ttu-id="eb116-130">`IHostIoCompletionManager`odpovídá `ICLRIoCompletionManager` rozhraní implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="eb116-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="eb116-131">CLR volá metody `IHostIoCompletionManager` k vytvoření vazby popisovače porty, které poskytuje hostitele a hostitele volá metody `ICLRIoCompletionManager` nahlásit dokončení vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="eb116-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb116-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb116-132">Requirements</span></span>  
 <span data-ttu-id="eb116-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb116-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb116-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb116-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb116-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb116-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb116-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb116-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb116-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb116-137">See Also</span></span>  
 [<span data-ttu-id="eb116-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eb116-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
