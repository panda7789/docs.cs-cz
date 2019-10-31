---
title: ITypeName::GetNames – metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
ms.openlocfilehash: 66934db3f1507262ffb2e9eec232f21574c29348
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095756"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="3186b-102">ITypeName::GetNames – metoda</span><span class="sxs-lookup"><span data-stu-id="3186b-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="3186b-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="3186b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3186b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3186b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3186b-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3186b-105">Requirements</span></span>  
 <span data-ttu-id="3186b-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3186b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3186b-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3186b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3186b-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3186b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3186b-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3186b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3186b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3186b-110">See also</span></span>

- [<span data-ttu-id="3186b-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="3186b-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
