---
title: ICorThreadpool::CorBindIoCompletionCallback – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5efd9811b0d5bfd16b802f0d504d69a4e7522833
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707853"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="42b98-102">ICorThreadpool::CorBindIoCompletionCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="42b98-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="42b98-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="42b98-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42b98-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="42b98-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42b98-105">Requirements</span></span>  
 <span data-ttu-id="42b98-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42b98-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42b98-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42b98-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42b98-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42b98-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42b98-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42b98-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b98-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42b98-110">See also</span></span>
- [<span data-ttu-id="42b98-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42b98-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
