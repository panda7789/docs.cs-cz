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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8897eda39a0ff5f1a11a95aeea4e2887912592ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519252"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="b7458-102">ICorRuntimeHost::LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="b7458-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="b7458-103">Získá počet zámků, které obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="b7458-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="b7458-104">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="b7458-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7458-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7458-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7458-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7458-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="b7458-107">[out] Ukazatel na počet zámků, které obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="b7458-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7458-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7458-108">Requirements</span></span>  
 <span data-ttu-id="b7458-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7458-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7458-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7458-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7458-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7458-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7458-112">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b7458-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7458-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7458-113">See also</span></span>
- [<span data-ttu-id="b7458-114">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7458-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
