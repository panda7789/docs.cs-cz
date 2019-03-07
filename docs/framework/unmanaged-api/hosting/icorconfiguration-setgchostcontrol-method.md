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
ms.openlocfilehash: a64922e1fe069d682f7ebc51040d06231a8b49c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484352"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="1441f-102">ICorConfiguration::SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="1441f-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="1441f-103">Nastaví rozhraní zpětného volání systému uvolňování paměti používané k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="1441f-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1441f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1441f-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1441f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1441f-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="1441f-106">[in] Ukazatel [igchostcontrol –](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objekt, který umožňuje požádat o hostiteli, chcete-li změnit omezení virtuální paměti systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1441f-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1441f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1441f-107">Requirements</span></span>  
 <span data-ttu-id="1441f-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1441f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1441f-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1441f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1441f-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1441f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1441f-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1441f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1441f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1441f-112">See also</span></span>
- [<span data-ttu-id="1441f-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1441f-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
