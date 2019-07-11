---
title: ICorThreadpool::CorUnregisterWait – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9ab5ca0a007422a2193d84a4915e2c0c67d855d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753194"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="d1403-102">ICorThreadpool::CorUnregisterWait – metoda</span><span class="sxs-lookup"><span data-stu-id="d1403-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="d1403-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d1403-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1403-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1403-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d1403-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1403-105">Requirements</span></span>  
 <span data-ttu-id="d1403-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1403-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1403-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1403-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1403-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1403-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1403-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1403-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1403-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1403-110">See also</span></span>

- [<span data-ttu-id="d1403-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1403-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
