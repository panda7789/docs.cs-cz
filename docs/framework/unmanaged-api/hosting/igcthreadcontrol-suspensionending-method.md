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
ms.openlocfilehash: d77380e35d8f5eee1e50b1030493e0b17cbadfba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713285"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="56f2d-102">IGCThreadControl::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="56f2d-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="56f2d-103">Upozorňuje hostitele, že modul runtime obnovuje po uvolnění paměti nebo jiných pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="56f2d-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f2d-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56f2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56f2d-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="56f2d-106">[in] Generování, na kterém byla provedena uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="56f2d-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f2d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56f2d-107">Remarks</span></span>  
 <span data-ttu-id="56f2d-108">Nelze změnit plán žádného vlákna během `SuspensionEnding` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="56f2d-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f2d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f2d-109">Requirements</span></span>  
 <span data-ttu-id="56f2d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f2d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56f2d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56f2d-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56f2d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56f2d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f2d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f2d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56f2d-114">See also</span></span>
- [<span data-ttu-id="56f2d-115">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56f2d-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
