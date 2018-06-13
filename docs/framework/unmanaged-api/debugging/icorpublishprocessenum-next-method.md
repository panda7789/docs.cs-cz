---
title: ICorPublishProcessEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19a10a527c37d93d00bec799fdaa12bb0ad3fdbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423868"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="e7d2a-102">ICorPublishProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e7d2a-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="e7d2a-103">Získá zadaný počet procesů z kolekce, počínaje na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="e7d2a-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7d2a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7d2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7d2a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e7d2a-106">[v] Počet procesů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="e7d2a-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="e7d2a-107">[out] Ukazatel na pole načíst [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objekty, z nichž každý představuje proces.</span><span class="sxs-lookup"><span data-stu-id="e7d2a-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e7d2a-108">[out] Ukazatel na počet procesů ve skutečnosti vrátila.</span><span class="sxs-lookup"><span data-stu-id="e7d2a-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="e7d2a-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="e7d2a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d2a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7d2a-110">Requirements</span></span>  
 <span data-ttu-id="e7d2a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d2a-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e7d2a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e7d2a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7d2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d2a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d2a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7d2a-115">See Also</span></span>  
 [<span data-ttu-id="e7d2a-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7d2a-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
