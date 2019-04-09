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
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124022"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="6fad7-102">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fad7-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="6fad7-103">Umožňuje modul CLR (CLR), která Udržovat informace kontextu zabezpečení implementovaná tímto hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6fad7-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6fad7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6fad7-104">Methods</span></span>  
  
|<span data-ttu-id="6fad7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6fad7-105">Method</span></span>|<span data-ttu-id="6fad7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6fad7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6fad7-107">Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="6fad7-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="6fad7-108">Získá klonu `IHostSecurityContext` instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="6fad7-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fad7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fad7-109">Remarks</span></span>  
 <span data-ttu-id="6fad7-110">Hostitele přístup můžete řídit všechny kódu tokeny vlákna CLR a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="6fad7-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="6fad7-111">Můžete také zajistit zabezpečení úplné informace o kontextu je předán přes asynchronní operace nebo body kódu s přístup ke kódu s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="6fad7-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> `IHostSecurityContext` <span data-ttu-id="6fad7-112">zapouzdřuje tato informace kontextu zabezpečení, což je neprůhledný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6fad7-112">encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="6fad7-113">Modul runtime zachycuje informace pomocí `Capture`, a přesouvá ji ve vláknu fondu pracovních procesů položky odeslání, spuštění finalizační metody a konstruktory modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="6fad7-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fad7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fad7-114">Requirements</span></span>  
 <span data-ttu-id="6fad7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fad7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fad7-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6fad7-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fad7-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fad7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6fad7-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6fad7-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6fad7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fad7-119">See also</span></span>

- [<span data-ttu-id="6fad7-120">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fad7-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="6fad7-121">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fad7-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6fad7-122">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="6fad7-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
