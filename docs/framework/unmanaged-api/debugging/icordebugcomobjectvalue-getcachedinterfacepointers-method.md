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
ms.openlocfilehash: 9d1d6d2f506086dd3204053b0b635da2e7cdc87e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783952"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="bc39b-102">ICorDebugComObjectValue::GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="bc39b-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="bc39b-103">Načte nezpracované ukazatele rozhraní uložené v mezipaměti v aktuální obálce pro vyvolané za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="bc39b-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc39b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc39b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc39b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc39b-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="bc39b-106">pro Hodnota, která určuje, zda metoda vrátí pouze prostředí Windows Runtime rozhraní (`IInspectable` rozhraní) nebo všechna rozhraní COM, která jsou uložena do mezipaměti pomocí obálky volání za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="bc39b-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="bc39b-107">pro Počet objektů, jejichž adresy mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="bc39b-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bc39b-108">mimo Ukazatel na počet hodnot `CORDB_ADDRESS` skutečně vrácených v `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="bc39b-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="bc39b-109">Ukazatel na počáteční adresu pole `CORDB_ADDRESS` hodnoty, které obsahují adresy objektů rozhraní uložených v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="bc39b-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc39b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc39b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc39b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc39b-111">Requirements</span></span>  
 <span data-ttu-id="bc39b-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc39b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc39b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc39b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc39b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc39b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc39b-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc39b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc39b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc39b-116">See also</span></span>

- [<span data-ttu-id="bc39b-117">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc39b-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="bc39b-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bc39b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
