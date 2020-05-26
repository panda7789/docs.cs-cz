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
ms.openlocfilehash: 90675d9be71342efa903767abbf63102b40a2c35
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804680"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="de982-102">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de982-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="de982-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) pracovat s porty dokončovacího vstupu a výstupu poskytovanými hostitelem.</span><span class="sxs-lookup"><span data-stu-id="de982-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de982-104">Metody</span><span class="sxs-lookup"><span data-stu-id="de982-104">Methods</span></span>  
  
|<span data-ttu-id="de982-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="de982-105">Method</span></span>|<span data-ttu-id="de982-106">Popis</span><span class="sxs-lookup"><span data-stu-id="de982-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de982-107">Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-107">Bind Method</span></span>](ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="de982-108">Váže popisovač k portu pro dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="de982-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="de982-109">CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-109">CloseIoCompletionPort Method</span></span>](ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="de982-110">Uzavře port, který byl vytvořen pomocí dřívějšího volání `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="de982-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="de982-111">CreateIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-111">CreateIoCompletionPort Method</span></span>](ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="de982-112">Požaduje, aby hostitel vytvořil nový port pro dokončení vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="de982-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="de982-113">GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-113">GetAvailableThreads Method</span></span>](ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="de982-114">Získá počet vláken dokončení v/v, která aktuálně nezpracovávají požadavky.</span><span class="sxs-lookup"><span data-stu-id="de982-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="de982-115">GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-115">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="de982-116">Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.</span><span class="sxs-lookup"><span data-stu-id="de982-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="de982-117">GetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-117">GetMaxThreads Method</span></span>](ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="de982-118">Získá maximální počet vláken, která může hostitel Allot na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="de982-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="de982-119">GetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-119">GetMinThreads Method</span></span>](ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="de982-120">Získá minimální počet vláken, která hostitel poskytuje pro vstupně-výstupní požadavky služby.</span><span class="sxs-lookup"><span data-stu-id="de982-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="de982-121">InitializeHostOverlapped – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-121">InitializeHostOverlapped Method</span></span>](ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="de982-122">Poskytuje hostiteli možnost inicializovat jakákoli vlastní data týkající se vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="de982-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="de982-123">SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="de982-124">Poskytuje hostitele s ukazatelem rozhraní na instanci [ICLRIoCompletionManager –](iclriocompletionmanager-interface.md) implementované modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="de982-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="de982-125">SetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-125">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="de982-126">Nastaví maximální počet vláken, která hostitel allots na požadavky na vstupně-výstupní operace služby.</span><span class="sxs-lookup"><span data-stu-id="de982-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="de982-127">SetMinThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="de982-127">SetMinThreads Method</span></span>](ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="de982-128">Nastaví minimální počet vláken, které by měl hostitel Allot na dokončení vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="de982-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de982-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de982-129">Remarks</span></span>  
 <span data-ttu-id="de982-130">`IHostIoCompletionManager`odpovídá `ICLRIoCompletionManager` rozhraní implementovanému modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="de982-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="de982-131">CLR volá metody `IHostIoCompletionManager` pro vázání popisovačů k portům, které poskytuje hostitel, a Hostitel volá metody `ICLRIoCompletionManager` pro hlášení dokončení vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="de982-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de982-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de982-132">Requirements</span></span>  
 <span data-ttu-id="de982-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de982-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de982-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="de982-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de982-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="de982-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de982-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de982-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de982-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="de982-137">See also</span></span>

- [<span data-ttu-id="de982-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="de982-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
