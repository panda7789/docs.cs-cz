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
ms.openlocfilehash: 59b37c30df6467439d04e367e13b0fc4ffff0ec6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422943"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="f67c6-102">ICorDebugObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f67c6-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="f67c6-103">Získá relativní virtuální adresy (RVAs) zadaný počet objektů z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="f67c6-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f67c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f67c6-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f67c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f67c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f67c6-106">[v] Počet objektů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f67c6-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f67c6-107">[out] Pole ukazatele, každý z nich odkazuje na objekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="f67c6-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f67c6-108">[out] Ukazatel na číslo ve skutečnosti vrácených objektů.</span><span class="sxs-lookup"><span data-stu-id="f67c6-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="f67c6-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="f67c6-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f67c6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f67c6-110">Requirements</span></span>  
 <span data-ttu-id="f67c6-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f67c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f67c6-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f67c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f67c6-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f67c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f67c6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f67c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67c6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f67c6-115">See Also</span></span>  
 
