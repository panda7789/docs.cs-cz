---
title: ICorThreadpool::CorQueueUserWorkItem – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 249571cbe49fdce720630e31d2da1641aa979624
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218690"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="745ff-102">ICorThreadpool::CorQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="745ff-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="745ff-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="745ff-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="745ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="745ff-104">Syntax</span></span>  
  
```  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="745ff-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="745ff-105">Requirements</span></span>  
 <span data-ttu-id="745ff-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="745ff-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="745ff-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="745ff-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="745ff-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="745ff-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="745ff-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="745ff-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745ff-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="745ff-110">See also</span></span>

- [<span data-ttu-id="745ff-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="745ff-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
