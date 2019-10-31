---
title: ICorDebugCode – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 8cb95fad4394e2ce9b7f922e720071d8c4434edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125594"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="7be5a-102">ICorDebugCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7be5a-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="7be5a-103">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7be5a-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7be5a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7be5a-104">Methods</span></span>  
  
|<span data-ttu-id="7be5a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-105">Method</span></span>|<span data-ttu-id="7be5a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7be5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7be5a-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="7be5a-108">Vytvoří zarážku v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="7be5a-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="7be5a-109">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="7be5a-110">Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="7be5a-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7be5a-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="7be5a-112">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="7be5a-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="7be5a-113">Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7be5a-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="7be5a-114">GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="7be5a-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="7be5a-115">Not implemented.</span></span>|  
|[<span data-ttu-id="7be5a-116">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="7be5a-117">Získá "ICorDebugFunction" spojený s tímto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7be5a-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7be5a-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="7be5a-119">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="7be5a-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="7be5a-120">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="7be5a-121">Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7be5a-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="7be5a-122">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="7be5a-123">Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="7be5a-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="7be5a-124">IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="7be5a-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="7be5a-125">Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="7be5a-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7be5a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7be5a-126">Remarks</span></span>  
 <span data-ttu-id="7be5a-127">Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód.</span><span class="sxs-lookup"><span data-stu-id="7be5a-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="7be5a-128">Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu přidružené buď žádný, nebo jeden objekt `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7be5a-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="7be5a-129">Objekt "ICorDebugFunction", který představuje nativní kód, může mít k sobě přidružen libovolný počet objektů `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7be5a-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7be5a-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7be5a-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be5a-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7be5a-131">Requirements</span></span>  
 <span data-ttu-id="7be5a-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be5a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be5a-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7be5a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7be5a-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7be5a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7be5a-135">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7be5a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be5a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7be5a-136">See also</span></span>

- [<span data-ttu-id="7be5a-137">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7be5a-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="7be5a-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7be5a-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
