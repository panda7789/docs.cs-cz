---
title: ICorThreadpool::CorGetAvailableThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: 40da8e67c705378c9e44398f6a0f519296da03e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133267"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="91870-102">ICorThreadpool::CorGetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="91870-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="91870-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="91870-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91870-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91870-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="91870-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91870-105">Requirements</span></span>  
 <span data-ttu-id="91870-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91870-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91870-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91870-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91870-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91870-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91870-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91870-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91870-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91870-110">See also</span></span>

- [<span data-ttu-id="91870-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91870-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
