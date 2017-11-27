---
title: "ICorDebugBlockingObjectEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c05420a54d7a79198e235a39e578bedf296b4fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="9cab2-102">ICorDebugBlockingObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9cab2-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="9cab2-103">Získá zadaný počet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="9cab2-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cab2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cab2-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingOjbect values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cab2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cab2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9cab2-106">[v] Počet objektů pro načtení.</span><span class="sxs-lookup"><span data-stu-id="9cab2-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="9cab2-107">[out] Pole ukazatele na [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="9cab2-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9cab2-108">[out] Ukazatel na počet objektů, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="9cab2-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cab2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9cab2-109">Return Value</span></span>  
 <span data-ttu-id="9cab2-110">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9cab2-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="9cab2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cab2-111">HRESULT</span></span>|<span data-ttu-id="9cab2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9cab2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cab2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cab2-113">S_OK</span></span>|<span data-ttu-id="9cab2-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9cab2-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9cab2-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9cab2-115">S_FALSE</span></span>|<span data-ttu-id="9cab2-116">`pceltFetched`není rovno `celt`.</span><span class="sxs-lookup"><span data-stu-id="9cab2-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cab2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cab2-117">Remarks</span></span>  
 <span data-ttu-id="9cab2-118">Tato metoda funguje jako typický COM enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9cab2-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="9cab2-119">Vstupní pole hodnoty musí být aspoň o velikosti `celt`.</span><span class="sxs-lookup"><span data-stu-id="9cab2-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="9cab2-120">Pole bude vyplněn buď Další `celt` hodnoty ve výčtu nebo s všechny zbývající hodnoty, pokud méně než `celt` zůstanou.</span><span class="sxs-lookup"><span data-stu-id="9cab2-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="9cab2-121">Po návratu tato metoda `pceltFetched` bude vyplněn počet hodnot, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="9cab2-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="9cab2-122">Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`, nebo pokud `pceltFetched` je neplatný ukazatel, výsledkem nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="9cab2-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cab2-123">I když [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktura není nutné uvolnit, rozhraní "ICorDebugValue" uvnitř této potřebuje k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="9cab2-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
-  
  
## <a name="requirements"></a><span data-ttu-id="9cab2-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cab2-124">Requirements</span></span>  
 <span data-ttu-id="9cab2-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cab2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cab2-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cab2-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cab2-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cab2-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cab2-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cab2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cab2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cab2-129">See Also</span></span>  
 [<span data-ttu-id="9cab2-130">ICorDebugDataTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cab2-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="9cab2-131">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cab2-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9cab2-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="9cab2-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
