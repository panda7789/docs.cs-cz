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
ms.openlocfilehash: b2c334c7a757c2f4044d08787bdae93ffc2804e4
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803887"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="e80e7-102">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e80e7-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="e80e7-103">Poskytuje metody, které umožňují přístup a řízení kontextu zabezpečení aktuálně prováděného vlákna.</span><span class="sxs-lookup"><span data-stu-id="e80e7-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e80e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e80e7-104">Methods</span></span>  
  
|<span data-ttu-id="e80e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-105">Method</span></span>|<span data-ttu-id="e80e7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e80e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e80e7-107">GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="e80e7-108">Získá požadovaná [IHostSecurityContext –](ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="e80e7-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="e80e7-109">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="e80e7-110">Požaduje, aby se kód spustil s použitím přihlašovacích údajů aktuální identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="e80e7-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="e80e7-111">OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="e80e7-112">Otevře volitelný přístupový token přidružený k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="e80e7-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="e80e7-113">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="e80e7-114">Ukončí zosobnění identity aktuálního uživatele a vrátí původní token vlákna.</span><span class="sxs-lookup"><span data-stu-id="e80e7-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="e80e7-115">SetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="e80e7-116">Nastaví kontext zabezpečení pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="e80e7-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="e80e7-117">SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e80e7-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="e80e7-118">Nastaví popisovač pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="e80e7-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e80e7-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e80e7-119">Remarks</span></span>  
 <span data-ttu-id="e80e7-120">Hostitel může řídit všechna přístupová oprávnění k tokenům vláken pomocí modulu CLR (Common Language Runtime) i uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="e80e7-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="e80e7-121">Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu.</span><span class="sxs-lookup"><span data-stu-id="e80e7-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="e80e7-122">`IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro CLR.</span><span class="sxs-lookup"><span data-stu-id="e80e7-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="e80e7-123">Modul CLR zpracovává kontext spravovaného vlákna interně.</span><span class="sxs-lookup"><span data-stu-id="e80e7-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="e80e7-124">Dotazuje se na konkrétní proces `IHostSecurityManager` v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="e80e7-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="e80e7-125">Ve vlákně finalizační metody při provádění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="e80e7-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="e80e7-126">Během provádění konstruktoru třídy a modulu.</span><span class="sxs-lookup"><span data-stu-id="e80e7-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="e80e7-127">V asynchronních bodech v pracovním vlákně v volání metody [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e80e7-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="e80e7-128">Při údržbě portů pro dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="e80e7-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e80e7-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e80e7-129">Requirements</span></span>  
 <span data-ttu-id="e80e7-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e80e7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e80e7-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e80e7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e80e7-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e80e7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e80e7-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e80e7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80e7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e80e7-134">See also</span></span>

- [<span data-ttu-id="e80e7-135">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e80e7-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e80e7-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="e80e7-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
