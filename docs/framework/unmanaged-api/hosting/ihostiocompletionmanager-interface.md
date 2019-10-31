---
title: IHostIoCompletionManager – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133850"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="fda0e-102">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda0e-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="fda0e-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s porty dokončovacího vstupu a výstupu poskytovanými hostitelem.</span><span class="sxs-lookup"><span data-stu-id="fda0e-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fda0e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fda0e-104">Methods</span></span>  
  
|<span data-ttu-id="fda0e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-105">Method</span></span>|<span data-ttu-id="fda0e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fda0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fda0e-107">Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="fda0e-108">Váže popisovač k portu pro dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="fda0e-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="fda0e-109">CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="fda0e-110">Uzavře port, který byl vytvořen pomocí předchozího volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="fda0e-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="fda0e-111">CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="fda0e-112">Požaduje, aby hostitel vytvořil nový port pro dokončení vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="fda0e-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="fda0e-113">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="fda0e-114">Získá počet vláken dokončení v/v, která aktuálně nezpracovávají požadavky.</span><span class="sxs-lookup"><span data-stu-id="fda0e-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="fda0e-115">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="fda0e-116">Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.</span><span class="sxs-lookup"><span data-stu-id="fda0e-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="fda0e-117">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="fda0e-118">Získá maximální počet vláken, která může hostitel Allot na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="fda0e-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="fda0e-119">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="fda0e-120">Získá minimální počet vláken, která hostitel poskytuje pro vstupně-výstupní požadavky služby.</span><span class="sxs-lookup"><span data-stu-id="fda0e-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="fda0e-121">InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="fda0e-122">Poskytuje hostiteli možnost inicializovat jakákoli vlastní data týkající se vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="fda0e-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="fda0e-123">SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="fda0e-124">Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRIoCompletionManager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implementované modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="fda0e-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="fda0e-125">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="fda0e-126">Nastaví maximální počet vláken, která hostitel allots na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="fda0e-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="fda0e-127">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0e-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="fda0e-128">Nastaví minimální počet vláken, které by měl hostitel Allot na dokončení vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="fda0e-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fda0e-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fda0e-129">Remarks</span></span>  
 <span data-ttu-id="fda0e-130">`IHostIoCompletionManager` odpovídá rozhraní `ICLRIoCompletionManager` implementovanému modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="fda0e-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="fda0e-131">CLR volá metody `IHostIoCompletionManager` pro vázání popisovačů k portům, které poskytuje hostitel, a Hostitel volá metody `ICLRIoCompletionManager` k hlášení dokončení vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="fda0e-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda0e-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fda0e-132">Requirements</span></span>  
 <span data-ttu-id="fda0e-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fda0e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fda0e-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fda0e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fda0e-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fda0e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fda0e-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fda0e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda0e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fda0e-137">See also</span></span>

- [<span data-ttu-id="fda0e-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="fda0e-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
