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
ms.openlocfilehash: 65eec8deb80caa017cb82b2c00a1f38ae487ae4d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489962"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="6dd2b-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6dd2b-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="6dd2b-103">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="6dd2b-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dd2b-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dd2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dd2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6dd2b-106">[in] Počet objektů typu GUID mapování se má načíst.</span><span class="sxs-lookup"><span data-stu-id="6dd2b-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6dd2b-107">[out] Pole ukazatelů, každý z nich odkazuje na [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekt, který mapuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID na jeho odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="6dd2b-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6dd2b-108">[out] Ukazatel na počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objektů skutečně vrácených v `values`.</span><span class="sxs-lookup"><span data-stu-id="6dd2b-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dd2b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dd2b-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd2b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dd2b-110">Requirements</span></span>  
 <span data-ttu-id="6dd2b-111">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd2b-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="6dd2b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6dd2b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dd2b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dd2b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dd2b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd2b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd2b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dd2b-115">See also</span></span>
- [<span data-ttu-id="6dd2b-116">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6dd2b-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="6dd2b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6dd2b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
