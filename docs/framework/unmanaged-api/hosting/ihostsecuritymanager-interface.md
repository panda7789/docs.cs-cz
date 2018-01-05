---
title: "IHostSecurityManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44f2272c0f4e1423c222a004559d7bbd58237d82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="46c48-102">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46c48-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="46c48-103">Poskytuje metody, které umožňují přístup a kontrolu nad kontext zabezpečení aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="46c48-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46c48-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46c48-104">Methods</span></span>  
  
|<span data-ttu-id="46c48-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-105">Method</span></span>|<span data-ttu-id="46c48-106">Popis</span><span class="sxs-lookup"><span data-stu-id="46c48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46c48-107">GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="46c48-108">Získá požadované [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="46c48-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="46c48-109">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="46c48-110">Požadavky kódu být spuštěn pomocí pověření aktuální identita uživatele.</span><span class="sxs-lookup"><span data-stu-id="46c48-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="46c48-111">OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="46c48-112">Otevře se token přístupu přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="46c48-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="46c48-113">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="46c48-114">Ukončí zosobnění aktuální identitu uživatele a vrátí původní tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="46c48-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="46c48-115">SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="46c48-116">Nastaví kontext zabezpečení pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="46c48-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="46c48-117">SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46c48-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="46c48-118">Nastaví popisovač pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="46c48-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46c48-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46c48-119">Remarks</span></span>  
 <span data-ttu-id="46c48-120">Hostitel přístup můžete řídit všechny kód vlákno tokeny modul common language runtime (CLR) i uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="46c48-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="46c48-121">Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="46c48-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="46c48-122">`IHostSecurityContext`zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="46c48-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="46c48-123">Modul CLR interně zpracovává kontextu spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="46c48-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="46c48-124">Vyžádá si konkrétní proces `IHostSecurityManager` v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="46c48-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="46c48-125">Ve vlákně finalizační metodu během provádění finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="46c48-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="46c48-126">Během provádění konstruktoru třídy a modulu.</span><span class="sxs-lookup"><span data-stu-id="46c48-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="46c48-127">V asynchronní bodů na pracovní vlákno ve voláních [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="46c48-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="46c48-128">V obslužném portů dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="46c48-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c48-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46c48-129">Requirements</span></span>  
 <span data-ttu-id="46c48-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c48-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c48-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46c48-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46c48-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46c48-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46c48-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c48-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c48-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c48-134">See Also</span></span>  
 [<span data-ttu-id="46c48-135">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46c48-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="46c48-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="46c48-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
