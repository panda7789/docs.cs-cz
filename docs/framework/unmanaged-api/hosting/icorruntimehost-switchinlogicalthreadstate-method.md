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
ms.openlocfilehash: 44973bcf98eb776735e0144ff1c2747b1445c5d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770893"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="57f66-102">ICorRuntimeHost::SwitchInLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="57f66-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="57f66-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="57f66-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57f66-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57f66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57f66-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="57f66-106">[in] Soubor cookie, který označuje fiber používat.</span><span class="sxs-lookup"><span data-stu-id="57f66-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f66-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57f66-107">Requirements</span></span>  
 <span data-ttu-id="57f66-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f66-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f66-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57f66-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57f66-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57f66-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57f66-111">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="57f66-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f66-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57f66-112">See also</span></span>

- [<span data-ttu-id="57f66-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57f66-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
