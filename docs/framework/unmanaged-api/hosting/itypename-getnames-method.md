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
ms.openlocfilehash: 615dad9000b15ed13783ca41cc3c9fe2b563e15c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842150"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="2529c-102">ITypeName::GetNames – metoda</span><span class="sxs-lookup"><span data-stu-id="2529c-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="2529c-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="2529c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2529c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2529c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2529c-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2529c-105">Requirements</span></span>  
 <span data-ttu-id="2529c-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2529c-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2529c-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2529c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2529c-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2529c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2529c-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2529c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2529c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2529c-110">See also</span></span>

- [<span data-ttu-id="2529c-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2529c-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
