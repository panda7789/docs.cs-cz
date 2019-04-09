---
title: IGCThreadControl::SuspensionEnding – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90b0cba50129bc728089e41ece5a30697cfc3bc5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144414"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="6692d-102">IGCThreadControl::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="6692d-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="6692d-103">Upozorňuje hostitele, že modul runtime obnovuje po uvolnění paměti nebo jiných pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="6692d-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6692d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6692d-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6692d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6692d-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="6692d-106">[in] Generování, na kterém byla provedena uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6692d-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6692d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6692d-107">Remarks</span></span>  
 <span data-ttu-id="6692d-108">Nelze změnit plán žádného vlákna během `SuspensionEnding` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6692d-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6692d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6692d-109">Requirements</span></span>  
 <span data-ttu-id="6692d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6692d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6692d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6692d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6692d-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6692d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6692d-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6692d-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6692d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6692d-114">See also</span></span>

- [<span data-ttu-id="6692d-115">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6692d-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
