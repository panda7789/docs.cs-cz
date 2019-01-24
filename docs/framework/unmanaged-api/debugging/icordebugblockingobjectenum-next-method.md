---
title: ICorDebugBlockingObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: def9d810917495165c7deda9e3dff158582a0e61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566252"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="9fadf-102">ICorDebugBlockingObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9fadf-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="9fadf-103">Získá zadaný počet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="9fadf-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fadf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fadf-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fadf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fadf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9fadf-106">[in] Počet objektů, které chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="9fadf-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="9fadf-107">[out] Pole ukazatelů na [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="9fadf-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9fadf-108">[out] Ukazatel na počet objektů, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="9fadf-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fadf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9fadf-109">Return Value</span></span>  
 <span data-ttu-id="9fadf-110">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9fadf-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="9fadf-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fadf-111">HRESULT</span></span>|<span data-ttu-id="9fadf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9fadf-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9fadf-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fadf-113">S_OK</span></span>|<span data-ttu-id="9fadf-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9fadf-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9fadf-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9fadf-115">S_FALSE</span></span>|<span data-ttu-id="9fadf-116">`pceltFetched` se nerovná `celt`.</span><span class="sxs-lookup"><span data-stu-id="9fadf-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fadf-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fadf-117">Remarks</span></span>  
 <span data-ttu-id="9fadf-118">Funkce v této metody, jako je typické COM enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9fadf-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="9fadf-119">Vstupní pole hodnoty musí být minimálně o velikosti `celt`.</span><span class="sxs-lookup"><span data-stu-id="9fadf-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="9fadf-120">Pole bude vyplněn buď na další `celt` hodnot ve výčtu nebo se všemi hodnotami zbývající Pokud méně než `celt` zůstanou.</span><span class="sxs-lookup"><span data-stu-id="9fadf-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="9fadf-121">Po návratu tato metoda `pceltFetched` se počet hodnot, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="9fadf-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="9fadf-122">Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`, nebo pokud `pceltFetched` je neplatný ukazatel, výsledek nedefinován.</span><span class="sxs-lookup"><span data-stu-id="9fadf-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fadf-123">I když [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) není nutné uvolnit strukturu, rozhraní "ICorDebugValue" uvnitř této nutné uvolnit.</span><span class="sxs-lookup"><span data-stu-id="9fadf-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fadf-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fadf-124">Requirements</span></span>  
 <span data-ttu-id="9fadf-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fadf-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fadf-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fadf-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fadf-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fadf-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fadf-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fadf-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fadf-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fadf-129">See also</span></span>
- [<span data-ttu-id="9fadf-130">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fadf-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="9fadf-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9fadf-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9fadf-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="9fadf-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
