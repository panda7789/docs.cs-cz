---
title: ICorThreadpool::CorCallOrQueueUserWorkItem – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCallOrQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallOrQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorCallOrQueueUserWorkItem method [.NET Framework hosting]
- CorCallOrQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: a2081223-84ca-4331-a8d3-9352f422f3e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62c81741b1260c20b25a0f49a33d3a20ebde24a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780413"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="1a1fe-102">ICorThreadpool::CorCallOrQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="1a1fe-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="1a1fe-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="1a1fe-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a1fe-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1a1fe-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a1fe-105">Requirements</span></span>  
 <span data-ttu-id="1a1fe-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1fe-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1fe-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a1fe-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a1fe-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a1fe-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a1fe-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1fe-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1fe-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a1fe-110">See also</span></span>

- [<span data-ttu-id="1a1fe-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a1fe-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
