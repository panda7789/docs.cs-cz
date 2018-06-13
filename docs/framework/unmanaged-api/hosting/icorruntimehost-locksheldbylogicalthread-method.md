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
ms.openlocfilehash: d46881b76685fd04f8bc5e3a67830e58f85cd774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436673"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="e934f-102">ICorRuntimeHost::LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="e934f-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="e934f-103">Načte číslo zámku, která obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="e934f-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="e934f-104">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e934f-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e934f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e934f-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e934f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e934f-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="e934f-107">[out] Ukazatel na číslo zámku, která obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="e934f-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e934f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e934f-108">Requirements</span></span>  
 <span data-ttu-id="e934f-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e934f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e934f-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e934f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e934f-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e934f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e934f-112">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e934f-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e934f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e934f-113">See Also</span></span>  
 [<span data-ttu-id="e934f-114">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e934f-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
