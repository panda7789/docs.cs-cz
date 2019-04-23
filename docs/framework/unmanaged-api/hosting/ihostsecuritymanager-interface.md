---
title: IHostSecurityManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223755"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="ab28f-102">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab28f-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="ab28f-103">Poskytuje metody, které umožňují přístup a kontrolu nad kontextu zabezpečení aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab28f-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab28f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab28f-104">Methods</span></span>  
  
|<span data-ttu-id="ab28f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-105">Method</span></span>|<span data-ttu-id="ab28f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ab28f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab28f-107">GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="ab28f-108">Získá požadovanou [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="ab28f-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="ab28f-109">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="ab28f-110">Požadavky, který kód spuštěn pomocí pověření aktuální identitu uživatele.</span><span class="sxs-lookup"><span data-stu-id="ab28f-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="ab28f-111">OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="ab28f-112">Otevře se token přístupu spojený s aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab28f-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="ab28f-113">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="ab28f-114">Zosobnění aktuální identitu uživatele se ukončí a vrátí původní token vlákna.</span><span class="sxs-lookup"><span data-stu-id="ab28f-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="ab28f-115">SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="ab28f-116">Nastaví kontext zabezpečení pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab28f-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="ab28f-117">SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ab28f-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="ab28f-118">Nastaví obslužnou rutinu pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab28f-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab28f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab28f-119">Remarks</span></span>  
 <span data-ttu-id="ab28f-120">Hostitele můžete řídit veškerý kód přístup k vláknu tokeny common language runtime (CLR) a kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="ab28f-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="ab28f-121">Můžete také zajistit zabezpečení úplné informace o kontextu je předán přes asynchronní operace nebo body kódu s přístup ke kódu s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="ab28f-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="ab28f-122">`IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, což je neprůhledný modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ab28f-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="ab28f-123">Modul CLR interně zpracovává kontext spravované vlákna.</span><span class="sxs-lookup"><span data-stu-id="ab28f-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="ab28f-124">Dotazy specifické pro proces `IHostSecurityManager` v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="ab28f-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="ab28f-125">Na finalizační podproces během spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ab28f-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="ab28f-126">Během provádění konstruktoru třídy a modulu.</span><span class="sxs-lookup"><span data-stu-id="ab28f-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="ab28f-127">V asynchronní body na pracovního vlákna ve voláních [ihostthreadpoolmanager::QueueUserWorkItem –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ab28f-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="ab28f-128">V obslužném portů dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="ab28f-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab28f-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab28f-129">Requirements</span></span>  
 <span data-ttu-id="ab28f-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab28f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab28f-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab28f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab28f-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab28f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab28f-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab28f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab28f-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab28f-134">See also</span></span>

- [<span data-ttu-id="ab28f-135">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab28f-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="ab28f-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ab28f-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
