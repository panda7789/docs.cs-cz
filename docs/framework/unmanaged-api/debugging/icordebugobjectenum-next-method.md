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
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178692"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="7982b-102">ICorDebugObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7982b-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="7982b-103">Získá relativní virtuální adresy (RVAs) zadaného počtu objektů z výčtu, počínaje aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="7982b-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7982b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7982b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7982b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7982b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7982b-106">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7982b-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="7982b-107">[out] Pole ukazatelů, z nichž každý odkazuje na objekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="7982b-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7982b-108">[out] Ukazatel na počet objektů skutečně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7982b-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="7982b-109">Tato hodnota může `celt` být null, pokud je jeden.</span><span class="sxs-lookup"><span data-stu-id="7982b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7982b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7982b-110">Requirements</span></span>  
 <span data-ttu-id="7982b-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7982b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7982b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7982b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7982b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7982b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7982b-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7982b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7982b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7982b-115">See also</span></span>
