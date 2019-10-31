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
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134787"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="512e3-102">IGCThreadControl::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="512e3-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="512e3-103">Upozorňuje hostitele, že modul runtime obnovuje vlákna po uvolnění paměti nebo jiném pozastavení.</span><span class="sxs-lookup"><span data-stu-id="512e3-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="512e3-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="512e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="512e3-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="512e3-106">pro Generování, na kterém bylo provedeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="512e3-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="512e3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="512e3-107">Remarks</span></span>  
 <span data-ttu-id="512e3-108">Během zpětného volání `SuspensionEnding` neplánujte žádná vlákna.</span><span class="sxs-lookup"><span data-stu-id="512e3-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="512e3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="512e3-109">Requirements</span></span>  
 <span data-ttu-id="512e3-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512e3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512e3-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="512e3-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="512e3-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="512e3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="512e3-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512e3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="512e3-114">See also</span></span>

- [<span data-ttu-id="512e3-115">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="512e3-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
