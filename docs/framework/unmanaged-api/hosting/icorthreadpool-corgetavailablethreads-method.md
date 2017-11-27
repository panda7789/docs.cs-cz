---
title: "ICorThreadpool::CorGetAvailableThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorGetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56d86cd9be5e5cee8d3fb1e2f79c8379a73b975a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="d9882-102">ICorThreadpool::CorGetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d9882-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="d9882-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="d9882-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9882-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d9882-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9882-105">Requirements</span></span>  
 <span data-ttu-id="d9882-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9882-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9882-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9882-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9882-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9882-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9882-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9882-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9882-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9882-110">See Also</span></span>  
 [<span data-ttu-id="d9882-111">Icorthreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9882-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
