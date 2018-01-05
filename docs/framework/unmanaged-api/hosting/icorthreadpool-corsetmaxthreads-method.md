---
title: "ICorThreadpool::CorSetMaxThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorSetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6b4b91dcae88e5dd8fcf0190689375a4310b02c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="2ac9b-102">ICorThreadpool::CorSetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="2ac9b-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="2ac9b-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2ac9b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ac9b-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2ac9b-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ac9b-105">Requirements</span></span>  
 <span data-ttu-id="2ac9b-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ac9b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ac9b-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ac9b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ac9b-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ac9b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ac9b-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ac9b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac9b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ac9b-110">See Also</span></span>  
 [<span data-ttu-id="2ac9b-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ac9b-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
