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
ms.openlocfilehash: 728a6ecab12038a81b98eed9675576d6c411590a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780011"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="20a19-102">ICorThreadpool::CorCreateTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="20a19-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="20a19-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="20a19-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20a19-104">Syntax</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="20a19-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20a19-105">Requirements</span></span>  
 <span data-ttu-id="20a19-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a19-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a19-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20a19-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20a19-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20a19-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20a19-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a19-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a19-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20a19-110">See also</span></span>

- [<span data-ttu-id="20a19-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20a19-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
