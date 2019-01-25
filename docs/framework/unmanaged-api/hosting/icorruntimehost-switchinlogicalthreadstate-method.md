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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eebfb98dfefd536998ef0c02d66b57d39414f0cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558732"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="e296c-102">ICorRuntimeHost::SwitchInLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="e296c-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="e296c-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e296c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e296c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e296c-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e296c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e296c-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e296c-106">[in] Soubor cookie, který označuje fiber používat.</span><span class="sxs-lookup"><span data-stu-id="e296c-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e296c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e296c-107">Requirements</span></span>  
 <span data-ttu-id="e296c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e296c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e296c-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e296c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e296c-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e296c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e296c-111">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e296c-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e296c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e296c-112">See also</span></span>
- [<span data-ttu-id="e296c-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e296c-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
