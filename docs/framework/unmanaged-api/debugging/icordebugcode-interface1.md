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
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788931"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="dc302-102">ICorDebugCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc302-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="dc302-103">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dc302-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc302-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dc302-104">Methods</span></span>  
  
|<span data-ttu-id="dc302-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-105">Method</span></span>|<span data-ttu-id="dc302-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dc302-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc302-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="dc302-108">Vytvoří zarážku v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="dc302-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="dc302-109">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="dc302-110">Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="dc302-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="dc302-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="dc302-112">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="dc302-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="dc302-113">Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dc302-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="dc302-114">GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="dc302-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="dc302-115">Not implemented.</span></span>|  
|[<span data-ttu-id="dc302-116">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="dc302-117">Získá "ICorDebugFunction" spojený s tímto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="dc302-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="dc302-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="dc302-119">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="dc302-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="dc302-120">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="dc302-121">Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="dc302-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="dc302-122">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="dc302-123">Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="dc302-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="dc302-124">IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="dc302-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="dc302-125">Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="dc302-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc302-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc302-126">Remarks</span></span>  
 <span data-ttu-id="dc302-127">Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód.</span><span class="sxs-lookup"><span data-stu-id="dc302-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="dc302-128">Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu přidružené buď žádný, nebo jeden objekt `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="dc302-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="dc302-129">Objekt "ICorDebugFunction", který představuje nativní kód, může mít k sobě přidružen libovolný počet objektů `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="dc302-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc302-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="dc302-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc302-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc302-131">Requirements</span></span>  
 <span data-ttu-id="dc302-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc302-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc302-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc302-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc302-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dc302-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc302-135">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc302-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc302-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc302-136">See also</span></span>

- [<span data-ttu-id="dc302-137">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc302-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="dc302-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dc302-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
