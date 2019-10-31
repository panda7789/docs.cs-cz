---
title: ICorRuntimeHost::SwitchInLogicalThreadState – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: b6569b5dab89a88a24cf2dfc873da9740e5af505
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133383"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="85d88-102">ICorRuntimeHost::SwitchInLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="85d88-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="85d88-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="85d88-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85d88-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85d88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85d88-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="85d88-106">pro Soubor cookie, který určuje vlákno, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="85d88-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d88-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85d88-107">Requirements</span></span>  
 <span data-ttu-id="85d88-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d88-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d88-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="85d88-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85d88-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="85d88-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85d88-111">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="85d88-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d88-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85d88-112">See also</span></span>

- [<span data-ttu-id="85d88-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85d88-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
