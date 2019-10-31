---
title: ICorRuntimeHost::LocksHeldByLogicalThread – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: f6ef7e06d94cb22d266949927cb15105b1602d3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139526"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="82474-102">ICorRuntimeHost::LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="82474-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="82474-103">Načte počet zámků, které aktuální vlákno uchovává.</span><span class="sxs-lookup"><span data-stu-id="82474-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="82474-104">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="82474-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82474-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82474-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82474-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82474-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="82474-107">mimo Ukazatel na počet zámků, které aktuální vlákno uchovává.</span><span class="sxs-lookup"><span data-stu-id="82474-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82474-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82474-108">Requirements</span></span>  
 <span data-ttu-id="82474-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82474-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82474-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="82474-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82474-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82474-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82474-112">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="82474-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82474-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82474-113">See also</span></span>

- [<span data-ttu-id="82474-114">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82474-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
