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
ms.openlocfilehash: f32381dc40a744157e46780e59b83efd63e58dcb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762640"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="464b2-102">ICorRuntimeHost::SwitchOutLogicalThreadState – metoda</span><span class="sxs-lookup"><span data-stu-id="464b2-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="464b2-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="464b2-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="464b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="464b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="464b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="464b2-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="464b2-106">mimo Soubor cookie, který označuje přepnutí optického vlákna.</span><span class="sxs-lookup"><span data-stu-id="464b2-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="464b2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="464b2-107">Requirements</span></span>  
 <span data-ttu-id="464b2-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="464b2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="464b2-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="464b2-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="464b2-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="464b2-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="464b2-111">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="464b2-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464b2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="464b2-112">See also</span></span>

- [<span data-ttu-id="464b2-113">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="464b2-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
