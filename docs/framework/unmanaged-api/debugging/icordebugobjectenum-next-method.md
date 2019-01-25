---
title: ICorDebugObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a5f21855ce83f5c1fb68637e3eeb6d3c831bce2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745151"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="974c8-102">ICorDebugObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="974c8-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="974c8-103">Získá relativních virtuálních adres (RVA) zadané počty objektů z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="974c8-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="974c8-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="974c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="974c8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="974c8-106">[in] Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="974c8-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="974c8-107">[out] Pole ukazatelů, každý z nich odkazuje na objekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="974c8-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="974c8-108">[out] Ukazatel na počet skutečně vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="974c8-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="974c8-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="974c8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="974c8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="974c8-110">Requirements</span></span>  
 <span data-ttu-id="974c8-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="974c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="974c8-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="974c8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="974c8-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="974c8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="974c8-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="974c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974c8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="974c8-115">See also</span></span>

