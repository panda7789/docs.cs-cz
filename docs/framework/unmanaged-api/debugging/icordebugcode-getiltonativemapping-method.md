---
title: ICorDebugCode::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13ec60999db88b9d7191a3866fcebe8098b4edee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411383"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="5b6b6-102">ICorDebugCode::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="5b6b6-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="5b6b6-103">Získá pole instancí "cor_debug_il_to_native_map –", která představuje mapování nativní posuny od společnosti Microsoft posune (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b6b6-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b6b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b6b6-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="5b6b6-106">[v] Velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="5b6b6-107">[out] Ukazatel na skutečný počet elementy, vrátí se v `map` pole.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="5b6b6-108">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, z nichž každý představuje mapování z MSIL posun na nativní posun.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="5b6b6-109">Není žádný řazení do pole elementů vrátila.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b6b6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b6b6-110">Remarks</span></span>  
 <span data-ttu-id="5b6b6-111">`GetILToNativeMapping` Metoda vrací výsledky, smysl pouze v případě, že tato instance "ICorDebugCode" představuje nativního kódu, který byl právě za běhu (JIT) zkompilovat z MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="5b6b6-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b6b6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b6b6-112">Requirements</span></span>  
 <span data-ttu-id="5b6b6-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b6b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b6b6-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b6b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b6b6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b6b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b6b6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b6b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6b6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b6b6-117">See Also</span></span>  
 [<span data-ttu-id="5b6b6-118">ICorDebugCode – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="5b6b6-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
