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
ms.openlocfilehash: 17afd0922930bc6db122e8dc07125dcafd483cf5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133299"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="caa1c-102">ICorThreadpool::CorCreateTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="caa1c-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="caa1c-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="caa1c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caa1c-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="caa1c-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caa1c-105">Requirements</span></span>  
 <span data-ttu-id="caa1c-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa1c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa1c-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="caa1c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="caa1c-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="caa1c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caa1c-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa1c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa1c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caa1c-110">See also</span></span>

- [<span data-ttu-id="caa1c-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa1c-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
