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
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501492"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="2e1c2-102">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1c2-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="2e1c2-103">Umožňuje modulu CLR (Common Language Runtime) zachovat informace o kontextu zabezpečení implementované hostitelem.</span><span class="sxs-lookup"><span data-stu-id="2e1c2-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e1c2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2e1c2-104">Methods</span></span>  
  
|<span data-ttu-id="2e1c2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e1c2-105">Method</span></span>|<span data-ttu-id="2e1c2-106">Description</span><span class="sxs-lookup"><span data-stu-id="2e1c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e1c2-107">Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1c2-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="2e1c2-108">Získá klon `IHostSecurityContext` instance vrácený voláním metody [IHostSecurityManager:: GetSecurityContext –](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="2e1c2-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e1c2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e1c2-109">Remarks</span></span>  
 <span data-ttu-id="2e1c2-110">Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="2e1c2-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="2e1c2-111">Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu.</span><span class="sxs-lookup"><span data-stu-id="2e1c2-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="2e1c2-112">`IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro modul runtime.</span><span class="sxs-lookup"><span data-stu-id="2e1c2-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="2e1c2-113">Modul runtime tyto informace zachytí pomocí `Capture` a přesune je mezi pracovními procesy odeslání položky pracovního procesu, provedení finalizační metody a konstruktory modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="2e1c2-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1c2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e1c2-114">Requirements</span></span>  
 <span data-ttu-id="2e1c2-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1c2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1c2-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e1c2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e1c2-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e1c2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e1c2-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e1c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1c2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e1c2-119">See also</span></span>

- [<span data-ttu-id="2e1c2-120">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1c2-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="2e1c2-121">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1c2-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="2e1c2-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2e1c2-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
