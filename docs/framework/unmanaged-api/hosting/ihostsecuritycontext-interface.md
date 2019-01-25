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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29499301260313ab796eee2be06a168f2ae48e4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712113"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="c6c8d-102">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6c8d-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="c6c8d-103">Umožňuje modul CLR (CLR), která Udržovat informace kontextu zabezpečení implementovaná tímto hostitelem.</span><span class="sxs-lookup"><span data-stu-id="c6c8d-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6c8d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c6c8d-104">Methods</span></span>  
  
|<span data-ttu-id="c6c8d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c6c8d-105">Method</span></span>|<span data-ttu-id="c6c8d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c6c8d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6c8d-107">Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="c6c8d-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="c6c8d-108">Získá klonu `IHostSecurityContext` instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6c8d-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6c8d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6c8d-109">Remarks</span></span>  
 <span data-ttu-id="c6c8d-110">Hostitele přístup můžete řídit všechny kódu tokeny vlákna CLR a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="c6c8d-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="c6c8d-111">Můžete také zajistit zabezpečení úplné informace o kontextu je předán přes asynchronní operace nebo body kódu s přístup ke kódu s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="c6c8d-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="c6c8d-112">`IHostSecurityContext` zapouzdřuje tato informace kontextu zabezpečení, což je neprůhledný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c6c8d-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="c6c8d-113">Modul runtime zachycuje informace pomocí `Capture`, a přesouvá ji ve vláknu fondu pracovních procesů položky odeslání, spuštění finalizační metody a konstruktory modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="c6c8d-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6c8d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6c8d-114">Requirements</span></span>  
 <span data-ttu-id="c6c8d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6c8d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6c8d-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6c8d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6c8d-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6c8d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6c8d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6c8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c8d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6c8d-119">See also</span></span>
- [<span data-ttu-id="c6c8d-120">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6c8d-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="c6c8d-121">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6c8d-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="c6c8d-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c6c8d-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
