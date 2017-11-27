---
title: ICorDebugCode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode
helpviewer_keywords: ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7813381c345db3d14318dddd93df1b491b46549e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="4eccd-102">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="4eccd-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="4eccd-103">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="4eccd-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4eccd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4eccd-104">Methods</span></span>  
  
|<span data-ttu-id="4eccd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-105">Method</span></span>|<span data-ttu-id="4eccd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4eccd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4eccd-107">Createbreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="4eccd-108">Vytvoří zarážku v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="4eccd-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="4eccd-109">Getaddress – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="4eccd-110">Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="4eccd-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="4eccd-111">Getcode – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="4eccd-112">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="4eccd-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="4eccd-113">Tato metoda je zastaralá; použít [icordebugcode2::getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="4eccd-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="4eccd-114">Getencremapsequencepoints – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="4eccd-115">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="4eccd-115">Not implemented.</span></span>|  
|[<span data-ttu-id="4eccd-116">Getfunction – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="4eccd-117">Získá "ICorDebugFunction" přidružený k tomuto `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="4eccd-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="4eccd-118">Getiltonativemapping – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="4eccd-119">Získá pole instancí "cor_debug_il_to_native_map –", která představuje mapování z MSIL posuny nativní posun.</span><span class="sxs-lookup"><span data-stu-id="4eccd-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="4eccd-120">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="4eccd-121">Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="4eccd-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="4eccd-122">Getversionnumber – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="4eccd-123">Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.</span><span class="sxs-lookup"><span data-stu-id="4eccd-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="4eccd-124">IsIL – metoda</span><span class="sxs-lookup"><span data-stu-id="4eccd-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="4eccd-125">Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="4eccd-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4eccd-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4eccd-126">Remarks</span></span>  
 <span data-ttu-id="4eccd-127">Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód.</span><span class="sxs-lookup"><span data-stu-id="4eccd-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="4eccd-128">Objekt "ICorDebugFunction", který představuje MSIL kód může mít nula nebo jedna `ICorDebugCode` objekty, které jsou s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="4eccd-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="4eccd-129">Objekt "ICorDebugFunction", který představuje nativního kódu může mít libovolný počet `ICorDebugCode` objekty, které jsou s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="4eccd-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4eccd-130">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4eccd-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eccd-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4eccd-131">Requirements</span></span>  
 <span data-ttu-id="4eccd-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eccd-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eccd-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4eccd-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4eccd-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4eccd-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eccd-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eccd-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eccd-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4eccd-136">See Also</span></span>  
    
 [<span data-ttu-id="4eccd-137">Icordebugcode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4eccd-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="4eccd-138">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="4eccd-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
