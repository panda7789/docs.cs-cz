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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186f5618cce7a70bc4fab55616a0f8b08025a81f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542532"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="05a27-102">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05a27-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="05a27-103">Poskytuje metody, které umožňují common language runtime (CLR) pro interakci s poskytované hostitelem portů dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="05a27-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05a27-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05a27-104">Methods</span></span>  
  
|<span data-ttu-id="05a27-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-105">Method</span></span>|<span data-ttu-id="05a27-106">Popis</span><span class="sxs-lookup"><span data-stu-id="05a27-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05a27-107">Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="05a27-108">Vytvoří vazbu popisovač na port dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="05a27-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="05a27-109">CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="05a27-110">Zavře port, který byl vytvořen pomocí dřívějším volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="05a27-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="05a27-111">CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="05a27-112">Požadavky, že hostitele, vytvořte nový port dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="05a27-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="05a27-113">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="05a27-114">Získá počet podprocesů dokončení vstupně-výstupních operací, které nejsou aktuálně zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="05a27-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="05a27-115">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="05a27-116">Získá velikost vlastní data, která si klade za cíl hostitele pro připojení k vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="05a27-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="05a27-117">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="05a27-118">Získá maximální počet vláken, která může přidělit hostitele služby vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="05a27-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="05a27-119">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="05a27-120">Získá minimální počet vláken, která obsahuje hostitele služby vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="05a27-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="05a27-121">InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="05a27-122">Poskytuje hostitele příležitost k inicializaci vlastních dat o požadavek na vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="05a27-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="05a27-123">SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="05a27-124">Poskytuje ukazatel rozhraní k hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementován modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="05a27-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="05a27-125">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="05a27-126">Nastaví maximální počet vláken, která allots hostitele služby vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="05a27-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="05a27-127">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="05a27-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="05a27-128">Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="05a27-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a27-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05a27-129">Remarks</span></span>  
 <span data-ttu-id="05a27-130">`IHostIoCompletionManager` odpovídá `ICLRIoCompletionManager` rozhraní implementované CLR.</span><span class="sxs-lookup"><span data-stu-id="05a27-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="05a27-131">CLR volá metody dané `IHostIoCompletionManager` zpracovává vytvořit vazbu na porty, které obsahuje hostitele a hostitele volá metody dané `ICLRIoCompletionManager` Oznámit dokončení vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="05a27-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05a27-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05a27-132">Requirements</span></span>  
 <span data-ttu-id="05a27-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05a27-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05a27-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05a27-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05a27-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05a27-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05a27-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05a27-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05a27-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05a27-137">See also</span></span>
- [<span data-ttu-id="05a27-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="05a27-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
