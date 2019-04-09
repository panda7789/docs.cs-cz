---
title: ICorThreadpool::CorCreateTimer – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69090618501abe7530ac7a04ae89a6bd3582e029
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111160"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="1f5be-102">ICorThreadpool::CorCreateTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="1f5be-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="1f5be-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="1f5be-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f5be-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1f5be-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f5be-105">Requirements</span></span>  
 <span data-ttu-id="1f5be-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f5be-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f5be-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f5be-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f5be-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f5be-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1f5be-109">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1f5be-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f5be-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f5be-110">See also</span></span>

- [<span data-ttu-id="1f5be-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f5be-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
