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
ms.openlocfilehash: f48c142b2b3742d01a8f796f11d5c9174529a041
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105816"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="f91dd-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f91dd-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="f91dd-103">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="f91dd-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f91dd-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f91dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f91dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f91dd-106">[in] Počet objektů typu GUID mapování se má načíst.</span><span class="sxs-lookup"><span data-stu-id="f91dd-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f91dd-107">[out] Pole ukazatelů, každý z nich odkazuje na [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekt, který mapuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID na jeho odpovídající objekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f91dd-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f91dd-108">[out] Ukazatel na počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objektů skutečně vrácených v `values`.</span><span class="sxs-lookup"><span data-stu-id="f91dd-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f91dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f91dd-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f91dd-110">Requirements</span></span>  
 **<span data-ttu-id="f91dd-111">Platformy:</span><span class="sxs-lookup"><span data-stu-id="f91dd-111">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="f91dd-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f91dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f91dd-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f91dd-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f91dd-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f91dd-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f91dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f91dd-115">See also</span></span>

- [<span data-ttu-id="f91dd-116">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f91dd-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="f91dd-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f91dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
