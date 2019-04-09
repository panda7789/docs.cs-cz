---
title: ICorConfiguration::SetGCHostControl – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a92058e8a394b95c690d19f1bafdddbed8246a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135990"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="9f231-102">ICorConfiguration::SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="9f231-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="9f231-103">Nastaví rozhraní zpětného volání systému uvolňování paměti používané k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="9f231-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f231-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f231-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f231-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f231-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="9f231-106">[in] Ukazatel [igchostcontrol –](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objekt, který umožňuje požádat o hostiteli, chcete-li změnit omezení virtuální paměti systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9f231-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f231-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f231-107">Requirements</span></span>  
 <span data-ttu-id="9f231-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f231-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f231-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f231-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f231-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f231-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9f231-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9f231-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f231-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f231-112">See also</span></span>

- [<span data-ttu-id="9f231-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f231-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
