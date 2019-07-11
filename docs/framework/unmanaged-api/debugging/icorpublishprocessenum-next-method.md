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
ms.openlocfilehash: 40a6376d4f4ffd09743441df1965d0a0f0d969b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764851"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="fda0d-102">ICorPublishProcessEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="fda0d-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="fda0d-103">Získá zadaný počet procesů z kolekce, spouští se na aktuální pozici kurzoru.</span><span class="sxs-lookup"><span data-stu-id="fda0d-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fda0d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fda0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fda0d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fda0d-106">[in] Počet procesů, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="fda0d-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="fda0d-107">[out] Načte ukazatel na pole [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objektů, z nichž každý představuje proces.</span><span class="sxs-lookup"><span data-stu-id="fda0d-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fda0d-108">[out] Ukazatel na počet skutečně vrácených procesů.</span><span class="sxs-lookup"><span data-stu-id="fda0d-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="fda0d-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="fda0d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda0d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fda0d-110">Requirements</span></span>  
 <span data-ttu-id="fda0d-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fda0d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fda0d-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="fda0d-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fda0d-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fda0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fda0d-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fda0d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda0d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fda0d-115">See also</span></span>

- [<span data-ttu-id="fda0d-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda0d-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
