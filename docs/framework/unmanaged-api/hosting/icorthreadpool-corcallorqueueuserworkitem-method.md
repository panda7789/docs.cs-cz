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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f18fcd5be15794449cc6c60d5217db702159e34d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436660"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="61cca-102">ICorThreadpool::CorCallOrQueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="61cca-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>
<span data-ttu-id="61cca-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="61cca-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61cca-104">Syntax</span></span>  
  
```  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="61cca-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61cca-105">Requirements</span></span>  
 <span data-ttu-id="61cca-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61cca-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61cca-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61cca-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61cca-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61cca-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61cca-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61cca-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cca-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="61cca-110">See Also</span></span>  
 [<span data-ttu-id="61cca-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61cca-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
