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
ms.openlocfilehash: c3ebe0bcd546feeeb0aa8c962f2b4c8b0562cb6f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760443"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="e5921-102">ICorThreadpool::CorBindIoCompletionCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="e5921-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="e5921-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e5921-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5921-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5921-104">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e5921-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5921-105">Requirements</span></span>  
 <span data-ttu-id="e5921-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5921-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5921-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e5921-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5921-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e5921-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5921-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5921-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5921-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5921-110">See also</span></span>

- [<span data-ttu-id="e5921-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5921-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
