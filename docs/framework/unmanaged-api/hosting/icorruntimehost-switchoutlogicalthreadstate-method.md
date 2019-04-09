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
ms.openlocfilehash: 1291d4e69843db7bd90af07291da415220d98807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131349"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="77db3-102">ICorRuntimeHost::SwitchOutLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="77db3-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="77db3-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="77db3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77db3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77db3-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77db3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77db3-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="77db3-106">[out] Soubor cookie, který označuje fiber probíhá přepnutí.</span><span class="sxs-lookup"><span data-stu-id="77db3-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77db3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77db3-107">Requirements</span></span>  
 <span data-ttu-id="77db3-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77db3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77db3-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77db3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77db3-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77db3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77db3-111">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="77db3-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77db3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77db3-112">See also</span></span>

- [<span data-ttu-id="77db3-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77db3-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
