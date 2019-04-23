---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a74ba2b5c1dc2340d20a793bcf3b14e2af234b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149614"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="bdf60-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="bdf60-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="bdf60-103">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdf60-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdf60-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bdf60-104">Methods</span></span>  
  
|<span data-ttu-id="bdf60-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-105">Method</span></span>|<span data-ttu-id="bdf60-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdf60-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="bdf60-108">Vytvoří nový unwinder zásobníku, který se spustí uvolnění z počáteční kontextu, (což není nutně listu vlákno).</span><span class="sxs-lookup"><span data-stu-id="bdf60-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="bdf60-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="bdf60-110">Vrátí seznam hodnot aktivní vlákno ID.</span><span class="sxs-lookup"><span data-stu-id="bdf60-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="bdf60-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="bdf60-112">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="bdf60-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="bdf60-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="bdf60-114">Vrátí cestu modulu z modulu Základní adresa.</span><span class="sxs-lookup"><span data-stu-id="bdf60-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="bdf60-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf60-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="bdf60-116">Vrátí poskytovatel symbolů pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="bdf60-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdf60-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdf60-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdf60-118">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdf60-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bdf60-119">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdf60-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf60-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdf60-120">Requirements</span></span>  
 <span data-ttu-id="bdf60-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf60-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf60-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdf60-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdf60-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf60-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf60-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf60-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf60-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdf60-125">See also</span></span>

- [<span data-ttu-id="bdf60-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bdf60-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bdf60-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="bdf60-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
