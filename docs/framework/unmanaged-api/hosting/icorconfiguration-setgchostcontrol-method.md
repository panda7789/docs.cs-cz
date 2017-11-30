---
title: "ICorConfiguration::SetGCHostControl – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33d01ff208e9814e73c7a658e41819348da6831a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="06335-102">ICorConfiguration::SetGCHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="06335-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="06335-103">Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="06335-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06335-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06335-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06335-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06335-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="06335-106">[v] Ukazatel na [igchostcontrol –](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objekt, který umožňuje uvolňování paměti požadavku na hostiteli a změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="06335-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06335-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06335-107">Requirements</span></span>  
 <span data-ttu-id="06335-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06335-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06335-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="06335-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06335-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06335-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06335-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06335-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06335-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="06335-112">See Also</span></span>  
 [<span data-ttu-id="06335-113">Icorconfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06335-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
