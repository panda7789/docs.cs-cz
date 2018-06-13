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
ms.openlocfilehash: 2c2500f013584ef4722ceaaaee91d5db54991639
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439296"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="10aa2-102">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10aa2-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="10aa2-103">Umožňuje modul CLR (CLR) k udržování informace kontextu zabezpečení implementované hostitele.</span><span class="sxs-lookup"><span data-stu-id="10aa2-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10aa2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="10aa2-104">Methods</span></span>  
  
|<span data-ttu-id="10aa2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="10aa2-105">Method</span></span>|<span data-ttu-id="10aa2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="10aa2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10aa2-107">Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="10aa2-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="10aa2-108">Získá klon `IHostSecurityContext` instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="10aa2-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10aa2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10aa2-109">Remarks</span></span>  
 <span data-ttu-id="10aa2-110">Hostitel můžou řídit všechny kódu přístup k vlákno tokeny kódem CLR i uživateli.</span><span class="sxs-lookup"><span data-stu-id="10aa2-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="10aa2-111">Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="10aa2-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="10aa2-112">`IHostSecurityContext` zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="10aa2-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="10aa2-113">Modul runtime zaznamená tato informace pomocí `Capture`, a přesouvá ji napříč vlákno fondu pracovní položka odesílání, provádění finalizační metodu a modul a třída konstruktory.</span><span class="sxs-lookup"><span data-stu-id="10aa2-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10aa2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10aa2-114">Requirements</span></span>  
 <span data-ttu-id="10aa2-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10aa2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10aa2-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10aa2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10aa2-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10aa2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10aa2-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10aa2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10aa2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="10aa2-119">See Also</span></span>  
 [<span data-ttu-id="10aa2-120">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10aa2-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="10aa2-121">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10aa2-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="10aa2-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="10aa2-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
