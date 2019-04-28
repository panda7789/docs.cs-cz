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
ms.openlocfilehash: c30623e53b57a78287b26d4a362793cfb32baede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750205"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="724f8-102">ICorDebugCode::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="724f8-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="724f8-103">Získává pole instancí "cor_debug_il_to_native_map –", které představují mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="724f8-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="724f8-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="724f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="724f8-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="724f8-106">[in] Velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="724f8-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="724f8-107">[out] Ukazatel na skutečný počet prvků vrácených v `map` pole.</span><span class="sxs-lookup"><span data-stu-id="724f8-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="724f8-108">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý představuje mapování z jazyka MSIL posun na nativní posun.</span><span class="sxs-lookup"><span data-stu-id="724f8-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="724f8-109">Neexistuje žádné řazení k poli prvků vrácených.</span><span class="sxs-lookup"><span data-stu-id="724f8-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="724f8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="724f8-110">Remarks</span></span>  
 <span data-ttu-id="724f8-111">`GetILToNativeMapping` Metoda vrátí smysluplné výsledky, pouze v případě, že tato instance "ICorDebugCode" představuje nativní kód, který byl just-in-time (JIT) kompilaci kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="724f8-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724f8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="724f8-112">Requirements</span></span>  
 <span data-ttu-id="724f8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="724f8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724f8-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="724f8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="724f8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="724f8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="724f8-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724f8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="724f8-117">See also</span></span>

- [<span data-ttu-id="724f8-118">Icordebugcode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="724f8-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
