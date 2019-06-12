---
title: ICorDebugComObjectValue::GetCachedInterfacePointers – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77e7f20aba1908a63d77b4ccada7fabacf55f7
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025845"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="91019-102">ICorDebugComObjectValue::GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="91019-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="91019-103">Získá ukazatele raw rozhraní ukládat do mezipaměti na aktuální obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="91019-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91019-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91019-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91019-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91019-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="91019-106">[in] Hodnota, která určuje, zda metoda vrátí pouze rozhraní Windows Runtime (`IInspectable` rozhraní) nebo jen rozhraní modelu COM, které jsou uložené v mezipaměti obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="91019-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="91019-107">[in] Počet objektů, jejichž adresy se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="91019-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="91019-108">[out] Ukazatel na počet `CORDB_ADDRESS` hodnoty ve skutečnosti vrácené v `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="91019-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="91019-109">Ukazatel na počáteční adresu pole `CORDB_ADDRESS` hodnoty, které obsahují adres do mezipaměti rozhraní objektů.</span><span class="sxs-lookup"><span data-stu-id="91019-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91019-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91019-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91019-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91019-111">Requirements</span></span>  
 <span data-ttu-id="91019-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91019-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91019-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91019-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91019-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91019-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91019-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91019-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91019-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91019-116">See also</span></span>

- [<span data-ttu-id="91019-117">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91019-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="91019-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="91019-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
