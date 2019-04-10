---
title: ICorThreadpool – rozhraní
ms.date: 03/30/2017
api_name:
- ICorThreadpool
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorThreadpool
helpviewer_keywords:
- ICorThreadpool interface [.NET Framework hosting]
ms.assetid: 18485a27-cae3-4c6a-baa8-f7df601122d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a30f10e322961d52c1fa726d5fd81e4c710a5835
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211761"
---
# <a name="icorthreadpool-interface"></a><span data-ttu-id="311a8-102">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="311a8-102">ICorThreadpool Interface</span></span>
<span data-ttu-id="311a8-103">Poskytuje metody pro přístup k fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="311a8-103">Provides methods for accessing the thread pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="311a8-104">Toto rozhraní je vyhrazená jenom pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-104">This interface is reserved for internal use only.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="311a8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="311a8-105">Methods</span></span>  
  
|<span data-ttu-id="311a8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-106">Method</span></span>|<span data-ttu-id="311a8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="311a8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="311a8-108">CorRegisterWaitForSingleObject – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-108">CorRegisterWaitForSingleObject Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corregisterwaitforsingleobject-method.md)|<span data-ttu-id="311a8-109">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-109">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-110">CorUnregisterWait – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-110">CorUnregisterWait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corunregisterwait-method.md)|<span data-ttu-id="311a8-111">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-111">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-112">CorQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-112">CorQueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md)|<span data-ttu-id="311a8-113">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-113">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-114">CorCreateTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-114">CorCreateTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corcreatetimer-method.md)|<span data-ttu-id="311a8-115">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-115">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-116">CorChangeTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-116">CorChangeTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corchangetimer-method.md)|<span data-ttu-id="311a8-117">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-117">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-118">CorDeleteTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-118">CorDeleteTimer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-cordeletetimer-method.md)|<span data-ttu-id="311a8-119">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-119">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-120">CorBindIoCompletionCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-120">CorBindIoCompletionCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corbindiocompletioncallback-method.md)|<span data-ttu-id="311a8-121">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-121">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-122">CorCallOrQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-122">CorCallOrQueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corcallorqueueuserworkitem-method.md)|<span data-ttu-id="311a8-123">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-123">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-124">CorSetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-124">CorSetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md)|<span data-ttu-id="311a8-125">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-125">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-126">CorGetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-126">CorGetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corgetmaxthreads-method.md)|<span data-ttu-id="311a8-127">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-127">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="311a8-128">CorGetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="311a8-128">CorGetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-corgetavailablethreads-method.md)|<span data-ttu-id="311a8-129">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="311a8-129">Reserved for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="311a8-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="311a8-130">Requirements</span></span>  
 <span data-ttu-id="311a8-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="311a8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311a8-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="311a8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="311a8-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="311a8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="311a8-134">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="311a8-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="311a8-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="311a8-135">See also</span></span>

- [<span data-ttu-id="311a8-136">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="311a8-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
