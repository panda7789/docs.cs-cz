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
ms.openlocfilehash: 265ab5ae03b7b42c4f5f429df5d659d60e55f18e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760716"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="33ea0-102">ICorRuntimeHost::LocksHeldByLogicalThread – metoda</span><span class="sxs-lookup"><span data-stu-id="33ea0-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="33ea0-103">Načte počet zámků, které aktuální vlákno uchovává.</span><span class="sxs-lookup"><span data-stu-id="33ea0-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="33ea0-104">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="33ea0-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ea0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33ea0-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33ea0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33ea0-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="33ea0-107">mimo Ukazatel na počet zámků, které aktuální vlákno uchovává.</span><span class="sxs-lookup"><span data-stu-id="33ea0-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ea0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33ea0-108">Requirements</span></span>  
 <span data-ttu-id="33ea0-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ea0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ea0-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="33ea0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33ea0-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="33ea0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33ea0-112">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="33ea0-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ea0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="33ea0-113">See also</span></span>

- [<span data-ttu-id="33ea0-114">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33ea0-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
