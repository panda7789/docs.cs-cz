---
title: ITypeName::GetModifiers – metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: c96764749a766f3b4bbff4cf6512677a47197f4c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095836"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="4e731-102">ITypeName::GetModifiers – metoda</span><span class="sxs-lookup"><span data-stu-id="4e731-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="4e731-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="4e731-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e731-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e731-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4e731-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e731-105">Requirements</span></span>  
 <span data-ttu-id="4e731-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e731-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e731-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e731-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e731-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e731-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e731-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e731-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e731-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e731-110">See also</span></span>

- [<span data-ttu-id="4e731-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4e731-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
