---
title: ICorThreadpool::CorSetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d84d5c45ea8e1af1da44480410692d46162810
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198241"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="f3aeb-102">ICorThreadpool::CorSetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="f3aeb-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="f3aeb-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f3aeb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3aeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3aeb-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f3aeb-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3aeb-105">Requirements</span></span>  
 <span data-ttu-id="f3aeb-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3aeb-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3aeb-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3aeb-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3aeb-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3aeb-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f3aeb-109">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f3aeb-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3aeb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3aeb-110">See also</span></span>

- [<span data-ttu-id="f3aeb-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3aeb-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
