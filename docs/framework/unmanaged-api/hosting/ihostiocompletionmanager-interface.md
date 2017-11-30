---
title: "IHostIoCompletionManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 847d4c3aa3e3da94b4aac4679ada047577379f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="f09aa-102">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f09aa-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="f09aa-103">Poskytuje metody, které povolit modul CLR (CLR) pro interakci s porty dokončení vstupně-výstupních operací od hostitele.</span><span class="sxs-lookup"><span data-stu-id="f09aa-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f09aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f09aa-104">Methods</span></span>  
  
|<span data-ttu-id="f09aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-105">Method</span></span>|<span data-ttu-id="f09aa-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f09aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f09aa-107">BIND – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="f09aa-108">Vytvoří vazbu k portu dokončení vstupně-výstupních operací popisovač.</span><span class="sxs-lookup"><span data-stu-id="f09aa-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="f09aa-109">Closeiocompletionport – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="f09aa-110">Zavření portů, která byla vytvořena pomocí dřívější volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="f09aa-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="f09aa-111">CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="f09aa-112">Počet požadavků, hostitele vytvořit nový port dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="f09aa-113">Getavailablethreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="f09aa-114">Získá počet vláken dokončení vstupně-výstupních operací, které nejsou aktuálně zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="f09aa-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="f09aa-115">Gethostoverlappedsize – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="f09aa-116">Získá velikost vlastní data, která hostitele chtít připojit k vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="f09aa-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="f09aa-117">Getmaxthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="f09aa-118">Získá maximální počet vláken, které můžete přidělit hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="f09aa-119">Getminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="f09aa-120">Získá minimální počet vláken, která poskytuje hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="f09aa-121">Initializehostoverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="f09aa-122">Poskytuje hostitele příležitost k inicializaci vlastních dat o požadavek vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="f09aa-123">Setclriocompletionmanager – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="f09aa-124">Poskytuje ukazatele rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f09aa-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="f09aa-125">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="f09aa-126">Nastaví maximální počet vláken, která allots hostitele se žádostí o službu vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="f09aa-127">Setminthreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f09aa-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="f09aa-128">Nastaví minimální počet vláken, která by měla přidělit hostitele na dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="f09aa-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f09aa-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f09aa-129">Remarks</span></span>  
 <span data-ttu-id="f09aa-130">`IHostIoCompletionManager`odpovídá `ICLRIoCompletionManager` rozhraní implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f09aa-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="f09aa-131">CLR volá metody `IHostIoCompletionManager` k vytvoření vazby popisovače porty, které poskytuje hostitele a hostitele volá metody `ICLRIoCompletionManager` nahlásit dokončení vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="f09aa-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f09aa-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f09aa-132">Requirements</span></span>  
 <span data-ttu-id="f09aa-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f09aa-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f09aa-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f09aa-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f09aa-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f09aa-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f09aa-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f09aa-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09aa-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="f09aa-137">See Also</span></span>  
 [<span data-ttu-id="f09aa-138">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="f09aa-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
