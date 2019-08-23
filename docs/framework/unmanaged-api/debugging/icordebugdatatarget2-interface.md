---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ea68474a1ee3a856b2e9393ff67d44f40a471c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911438"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="c22fe-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c22fe-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="c22fe-103">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c22fe-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c22fe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c22fe-104">Methods</span></span>  
  
|<span data-ttu-id="c22fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-105">Method</span></span>|<span data-ttu-id="c22fe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c22fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c22fe-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="c22fe-108">Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).</span><span class="sxs-lookup"><span data-stu-id="c22fe-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="c22fe-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="c22fe-110">Vrátí seznam identifikátorů aktivních vláken.</span><span class="sxs-lookup"><span data-stu-id="c22fe-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="c22fe-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="c22fe-112">Vrátí základní adresu modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="c22fe-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="c22fe-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="c22fe-114">Vrátí cestu modulu ze základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="c22fe-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="c22fe-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="c22fe-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="c22fe-116">Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="c22fe-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c22fe-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c22fe-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c22fe-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c22fe-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c22fe-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="c22fe-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c22fe-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c22fe-120">Requirements</span></span>  
 <span data-ttu-id="c22fe-121">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c22fe-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c22fe-122">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c22fe-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c22fe-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c22fe-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c22fe-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c22fe-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22fe-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c22fe-125">See also</span></span>

- [<span data-ttu-id="c22fe-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c22fe-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c22fe-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="c22fe-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
