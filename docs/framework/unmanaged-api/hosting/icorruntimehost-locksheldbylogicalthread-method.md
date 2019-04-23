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
ms.openlocfilehash: 90af015de4428f75330de89978a7fc0a4b26750b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144193"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="f2060-102">ICorRuntimeHost::LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="f2060-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="f2060-103">Získá počet zámků, které obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f2060-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="f2060-104">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="f2060-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2060-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2060-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2060-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2060-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="f2060-107">[out] Ukazatel na počet zámků, které obsahuje aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f2060-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2060-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2060-108">Requirements</span></span>  
 <span data-ttu-id="f2060-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2060-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2060-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2060-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2060-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2060-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2060-112">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f2060-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2060-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2060-113">See also</span></span>

- [<span data-ttu-id="f2060-114">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2060-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
