---
title: IHostSecurityContext – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: bf8e725908177d9a15407b096f68cbcb947c7a01
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804145"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="d11a5-102">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d11a5-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="d11a5-103">Umožňuje modulu CLR (Common Language Runtime) zachovat informace o kontextu zabezpečení implementované hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d11a5-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d11a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d11a5-104">Methods</span></span>  
  
|<span data-ttu-id="d11a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d11a5-105">Method</span></span>|<span data-ttu-id="d11a5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d11a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d11a5-107">Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="d11a5-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="d11a5-108">Získá klon `IHostSecurityContext` instance vrácený voláním metody [IHostSecurityManager:: GetSecurityContext –](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="d11a5-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d11a5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d11a5-109">Remarks</span></span>  
 <span data-ttu-id="d11a5-110">Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="d11a5-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="d11a5-111">Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu.</span><span class="sxs-lookup"><span data-stu-id="d11a5-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="d11a5-112">`IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d11a5-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="d11a5-113">Modul runtime tyto informace zachytí pomocí `Capture` a přesune je mezi pracovními procesy odeslání položky pracovního procesu, provedení finalizační metody a konstruktory modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="d11a5-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d11a5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d11a5-114">Requirements</span></span>  
 <span data-ttu-id="d11a5-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d11a5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d11a5-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d11a5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d11a5-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d11a5-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d11a5-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d11a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11a5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d11a5-119">See also</span></span>

- [<span data-ttu-id="d11a5-120">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d11a5-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="d11a5-121">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d11a5-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d11a5-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d11a5-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
