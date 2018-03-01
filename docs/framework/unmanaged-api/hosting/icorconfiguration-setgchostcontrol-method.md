---
title: "ICorConfiguration::SetGCHostControl – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98f36fea9705d212b01a0220cca321192b8193d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="99b32-102">ICorConfiguration::SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="99b32-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="99b32-103">Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="99b32-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99b32-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99b32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99b32-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="99b32-106">[v] Ukazatel na [igchostcontrol –](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objekt, který umožňuje uvolňování paměti požadavku na hostiteli a změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="99b32-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99b32-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99b32-107">Requirements</span></span>  
 <span data-ttu-id="99b32-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99b32-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b32-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99b32-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99b32-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99b32-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99b32-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b32-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b32-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="99b32-112">See Also</span></span>  
 [<span data-ttu-id="99b32-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99b32-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
