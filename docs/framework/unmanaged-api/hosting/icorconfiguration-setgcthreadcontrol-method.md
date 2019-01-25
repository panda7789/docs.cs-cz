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
ms.openlocfilehash: 12cce87f7c92224dd83e4a51faedda616f0bbc39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676806"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="1968b-102">ICorConfiguration::SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="1968b-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="1968b-103">Nastaví rozhraní zpětného volání pro plánování vláken pro úlohy – modul runtime, které by se jinak zablokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1968b-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1968b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1968b-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1968b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1968b-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="1968b-106">[in] Ukazatel [igcthreadcontrol –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objektu, která upozorňuje hostitele o pozastavení vláken pro úlohy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1968b-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1968b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1968b-107">Remarks</span></span>  
 <span data-ttu-id="1968b-108">Zvolit hostitele v rámci [igcthreadcontrol::threadisblockingforsuspension –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) zpětné volání, jestli se má plánovanou zkoušku přeplánovat vlákno.</span><span class="sxs-lookup"><span data-stu-id="1968b-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1968b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1968b-109">Requirements</span></span>  
 <span data-ttu-id="1968b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1968b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1968b-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1968b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1968b-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1968b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1968b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1968b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1968b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1968b-114">See also</span></span>
- [<span data-ttu-id="1968b-115">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1968b-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
