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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893474"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="ffe23-102">ICorDebugCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffe23-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="ffe23-103">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffe23-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ffe23-104">Methods</span></span>  
  
|<span data-ttu-id="ffe23-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-105">Method</span></span>|<span data-ttu-id="ffe23-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ffe23-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffe23-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="ffe23-108">Vytvoří zarážku v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="ffe23-109">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="ffe23-110">Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="ffe23-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="ffe23-111">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="ffe23-112">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="ffe23-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="ffe23-113">Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ffe23-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="ffe23-114">GetEnCRemapSequencePoints – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="ffe23-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="ffe23-115">Not implemented.</span></span>|  
|[<span data-ttu-id="ffe23-116">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="ffe23-117">Načte "ICorDebugFunction" spojený s tímto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="ffe23-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="ffe23-118">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="ffe23-119">Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="ffe23-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="ffe23-120">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="ffe23-121">Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="ffe23-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="ffe23-122">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="ffe23-123">Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="ffe23-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="ffe23-124">IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="ffe23-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="ffe23-125">Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="ffe23-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffe23-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffe23-126">Remarks</span></span>  
 <span data-ttu-id="ffe23-127">Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód.</span><span class="sxs-lookup"><span data-stu-id="ffe23-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="ffe23-128">Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu `ICorDebugCode` přidružené buď nula, nebo jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="ffe23-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="ffe23-129">K objektu "ICorDebugFunction", který představuje nativní kód, může být přidružen `ICorDebugCode` libovolný počet objektů.</span><span class="sxs-lookup"><span data-stu-id="ffe23-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffe23-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe23-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffe23-131">Requirements</span></span>  
 <span data-ttu-id="ffe23-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffe23-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe23-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ffe23-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffe23-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ffe23-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffe23-135">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe23-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe23-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffe23-136">See also</span></span>

- [<span data-ttu-id="ffe23-137">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffe23-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="ffe23-138">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffe23-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
