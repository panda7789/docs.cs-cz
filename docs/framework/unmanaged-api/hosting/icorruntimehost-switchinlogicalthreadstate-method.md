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
ms.openlocfilehash: d0836d47c364a815ea3de9b991fe788815a1b36c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436686"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="9861c-102">ICorRuntimeHost::SwitchInLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="9861c-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="9861c-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="9861c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9861c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9861c-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9861c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9861c-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="9861c-106">[v] Soubor cookie, který označuje fiber používat.</span><span class="sxs-lookup"><span data-stu-id="9861c-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9861c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9861c-107">Requirements</span></span>  
 <span data-ttu-id="9861c-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9861c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9861c-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9861c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9861c-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9861c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9861c-111">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9861c-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9861c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9861c-112">See Also</span></span>  
 [<span data-ttu-id="9861c-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9861c-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
