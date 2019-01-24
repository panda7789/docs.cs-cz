---
title: ICorThreadpool::CorGetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33cbbf5d9be682b82b7e21034b1db206f0ba4ec5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646188"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="d5a03-102">ICorThreadpool::CorGetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d5a03-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="d5a03-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d5a03-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5a03-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5a03-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5a03-105">Requirements</span></span>  
 <span data-ttu-id="d5a03-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a03-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a03-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5a03-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5a03-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5a03-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5a03-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a03-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a03-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5a03-110">See also</span></span>
- [<span data-ttu-id="d5a03-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5a03-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
