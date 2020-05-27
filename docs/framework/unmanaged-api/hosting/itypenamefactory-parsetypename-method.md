---
title: ITypeNameFactory::ParseTypeName – metoda
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 1d00d150f98e44fb5c6484378266b7d9b238f4a9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008583"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="ba601-102">ITypeNameFactory::ParseTypeName – metoda</span><span class="sxs-lookup"><span data-stu-id="ba601-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="ba601-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="ba601-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba601-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba601-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ba601-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba601-105">Requirements</span></span>  
 <span data-ttu-id="ba601-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba601-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba601-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba601-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba601-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba601-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba601-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba601-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba601-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba601-110">See also</span></span>

- [<span data-ttu-id="ba601-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ba601-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
