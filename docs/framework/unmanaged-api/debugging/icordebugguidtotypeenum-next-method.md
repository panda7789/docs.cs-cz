---
title: ICorDebugGuidToTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f334b4a28b0573fa938c2fda340c0c03175ff18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756875"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="374dd-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="374dd-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="374dd-103">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="374dd-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="374dd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="374dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="374dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="374dd-106">[in] Počet objektů typu GUID mapování se má načíst.</span><span class="sxs-lookup"><span data-stu-id="374dd-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="374dd-107">[out] Pole ukazatelů, každý z nich odkazuje [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekt, který se mapuje na jeho odpovídající objekt ICorDebugType identifikátor GUID Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="374dd-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="374dd-108">[out] Ukazatel na počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objektů skutečně vrácených v `values`.</span><span class="sxs-lookup"><span data-stu-id="374dd-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="374dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="374dd-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="374dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="374dd-110">Requirements</span></span>  
 <span data-ttu-id="374dd-111">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="374dd-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="374dd-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="374dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="374dd-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="374dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="374dd-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="374dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="374dd-115">See also</span></span>

- [<span data-ttu-id="374dd-116">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="374dd-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="374dd-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="374dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
