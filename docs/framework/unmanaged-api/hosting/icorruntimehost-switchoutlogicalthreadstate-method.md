---
title: ICorRuntimeHost::SwitchOutLogicalThreadState – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33729e9efa999eb276140ddd2571a4844e15dd6d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770822"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="8c54e-102">ICorRuntimeHost::SwitchOutLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="8c54e-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="8c54e-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="8c54e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c54e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c54e-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c54e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c54e-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="8c54e-106">[out] Soubor cookie, který označuje fiber probíhá přepnutí.</span><span class="sxs-lookup"><span data-stu-id="8c54e-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c54e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c54e-107">Requirements</span></span>  
 <span data-ttu-id="8c54e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c54e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c54e-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c54e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c54e-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c54e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c54e-111">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8c54e-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c54e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c54e-112">See also</span></span>

- [<span data-ttu-id="8c54e-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c54e-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
