---
title: "ICorDebugGuidToTypeEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 277661c8c5490b5c1f68cb8fdaf1eff5a020250f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="7301b-102">ICorDebugGuidToTypeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7301b-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="7301b-103">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které mapují identifikátory GUID na typ informace.</span><span class="sxs-lookup"><span data-stu-id="7301b-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7301b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7301b-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7301b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7301b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7301b-106">[v] Počet objektů mapování typu GUID mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7301b-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7301b-107">[out] Ukazatele, každý z nich odkazuje na pole [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekt, který se mapuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID do její odpovídající ICorDebugType objektu.</span><span class="sxs-lookup"><span data-stu-id="7301b-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7301b-108">[out] Ukazatel na počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekty ve skutečnosti, vrátí se v `values`.</span><span class="sxs-lookup"><span data-stu-id="7301b-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7301b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7301b-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7301b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7301b-110">Requirements</span></span>  
 <span data-ttu-id="7301b-111">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7301b-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="7301b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7301b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7301b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7301b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7301b-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7301b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7301b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7301b-115">See Also</span></span>  
 [<span data-ttu-id="7301b-116">ICorDebugGuidToTypeEnum – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="7301b-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [<span data-ttu-id="7301b-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7301b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
