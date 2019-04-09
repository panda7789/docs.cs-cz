---
title: ICorConfiguration::SetGCThreadControl – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135834"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="970e9-102">ICorConfiguration::SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="970e9-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="970e9-103">Nastaví rozhraní zpětného volání pro plánování vláken pro úlohy – modul runtime, které by se jinak zablokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="970e9-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="970e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="970e9-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="970e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="970e9-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="970e9-106">[in] Ukazatel [igcthreadcontrol –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objektu, která upozorňuje hostitele o pozastavení vláken pro úlohy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="970e9-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="970e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="970e9-107">Remarks</span></span>  
 <span data-ttu-id="970e9-108">Zvolit hostitele v rámci [igcthreadcontrol::threadisblockingforsuspension –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) zpětné volání, jestli se má plánovanou zkoušku přeplánovat vlákno.</span><span class="sxs-lookup"><span data-stu-id="970e9-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="970e9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="970e9-109">Requirements</span></span>  
 <span data-ttu-id="970e9-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="970e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="970e9-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="970e9-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="970e9-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="970e9-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="970e9-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="970e9-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="970e9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="970e9-114">See also</span></span>

- [<span data-ttu-id="970e9-115">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="970e9-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
