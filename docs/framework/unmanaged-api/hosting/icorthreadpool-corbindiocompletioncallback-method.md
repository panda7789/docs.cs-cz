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
ms.openlocfilehash: ca1e594250c5447e6a2313843095010739a0cadb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436647"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="39836-102">ICorThreadpool::CorBindIoCompletionCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="39836-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="39836-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="39836-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39836-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="39836-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39836-105">Requirements</span></span>  
 <span data-ttu-id="39836-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39836-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39836-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39836-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39836-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39836-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39836-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39836-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39836-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="39836-110">See Also</span></span>  
 [<span data-ttu-id="39836-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39836-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
