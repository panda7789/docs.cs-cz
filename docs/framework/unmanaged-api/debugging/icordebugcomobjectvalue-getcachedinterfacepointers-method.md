---
title: "ICorDebugComObjectValue::GetCachedInterfacePointers – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfacePointers
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="eec07-102">ICorDebugComObjectValue::GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="eec07-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="eec07-103">Získá ukazatele nezpracovaná rozhraní ukládat do mezipaměti na aktuální obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="eec07-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eec07-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eec07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eec07-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="eec07-106">[v] Hodnotu, která určuje, zda metoda vrátí pouze [!INCLUDE[wrt](../../../../includes/wrt-md.md)] rozhraní (`IInspectable` rozhraní) nebo všech rozhraní modelu COM, které jsou uloženy v mezipaměti obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="eec07-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="eec07-107">[v] Počet objektů, jejichž adresy jsou mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="eec07-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="eec07-108">[out] Ukazatel na počet `CORDB_ADDRESS` hodnot vrácených ve skutečnosti v `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="eec07-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="eec07-109">Ukazatel na počáteční adresa pole `CORDB_ADDRESS` hodnoty, které obsahují adresy uložené v mezipaměti objektů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eec07-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eec07-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eec07-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec07-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eec07-111">Requirements</span></span>  
 <span data-ttu-id="eec07-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eec07-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec07-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eec07-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eec07-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec07-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eec07-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec07-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec07-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="eec07-116">See Also</span></span>  
 [<span data-ttu-id="eec07-117">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eec07-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="eec07-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="eec07-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
