---
title: "ICorConfiguration::SetGCThreadControl – metoda"
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
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b6b28b67f924df4d7f587d0364bce2a853f60b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="079ea-102">ICorConfiguration::SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="079ea-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="079ea-103">Nastaví zpětné volání rozhraní pro plánování vláken pro úlohy – modul runtime, které by jinak blokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="079ea-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079ea-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="079ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="079ea-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="079ea-106">[v] Ukazatel na [igcthreadcontrol –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objekt, který upozorní hostitele o pozastavení vláken pro úlohy – modul runtime.</span><span class="sxs-lookup"><span data-stu-id="079ea-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="079ea-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="079ea-107">Remarks</span></span>  
 <span data-ttu-id="079ea-108">Hostitel rozhodnout, že v rámci [igcthreadcontrol::threadisblockingforsuspension –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) zpětného volání jestli se má změnit plán naplánovaných vlákna.</span><span class="sxs-lookup"><span data-stu-id="079ea-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="079ea-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="079ea-109">Requirements</span></span>  
 <span data-ttu-id="079ea-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="079ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="079ea-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="079ea-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="079ea-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="079ea-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="079ea-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="079ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079ea-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="079ea-114">See Also</span></span>  
 [<span data-ttu-id="079ea-115">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="079ea-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
