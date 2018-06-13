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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c4867760807af1bc16f7935923cc2b89c1bfba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436891"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="d9b66-102">ICorThreadpool::CorGetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d9b66-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="d9b66-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d9b66-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9b66-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d9b66-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9b66-105">Requirements</span></span>  
 <span data-ttu-id="d9b66-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b66-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b66-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9b66-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9b66-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9b66-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b66-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b66-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b66-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9b66-110">See Also</span></span>  
 [<span data-ttu-id="d9b66-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9b66-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
