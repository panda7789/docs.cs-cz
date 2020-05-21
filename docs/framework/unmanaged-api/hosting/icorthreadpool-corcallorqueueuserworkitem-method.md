---
title: ICorThreadpool::CorCallOrQueueUserWorkItem – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCallOrQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallOrQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorCallOrQueueUserWorkItem method [.NET Framework hosting]
- CorCallOrQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: a2081223-84ca-4331-a8d3-9352f422f3e7
topic_type:
- apiref
ms.openlocfilehash: a2d2d6307136f0f8983e409d9f17fbcae1c55705
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760322"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="a41d3-102">ICorThreadpool::CorCallOrQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="a41d3-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="a41d3-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="a41d3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a41d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a41d3-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a41d3-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a41d3-105">Requirements</span></span>  
 <span data-ttu-id="a41d3-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a41d3-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a41d3-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a41d3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a41d3-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a41d3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a41d3-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a41d3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a41d3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a41d3-110">See also</span></span>

- [<span data-ttu-id="a41d3-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a41d3-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
