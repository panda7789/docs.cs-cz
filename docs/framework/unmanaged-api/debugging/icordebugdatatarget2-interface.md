---
title: "Rozhraní ICorDebugDataTarget2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 034e7d46c1b38aecdab18ea3a7d3b149b3d59369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="66ff1-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="66ff1-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="66ff1-103">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66ff1-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66ff1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66ff1-104">Methods</span></span>  
  
|<span data-ttu-id="66ff1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66ff1-105">Method</span></span>|<span data-ttu-id="66ff1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="66ff1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66ff1-107">Metoda CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="66ff1-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="66ff1-108">Vytvoří nový unwinder zásobníku, která se spouští unwinding z kontextu počáteční (který není nutně listu vlákna).</span><span class="sxs-lookup"><span data-stu-id="66ff1-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="66ff1-109">Metoda EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="66ff1-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="66ff1-110">Vrátí seznam aktivních vláken ID.</span><span class="sxs-lookup"><span data-stu-id="66ff1-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="66ff1-111">Metoda GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="66ff1-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="66ff1-112">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="66ff1-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="66ff1-113">Metoda GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="66ff1-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="66ff1-114">Vrátí cestu modul z modulu základní adresu.</span><span class="sxs-lookup"><span data-stu-id="66ff1-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="66ff1-115">Metoda GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="66ff1-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="66ff1-116">Vrátí symbol zprostředkovatele pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="66ff1-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66ff1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66ff1-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66ff1-118">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="66ff1-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="66ff1-119">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66ff1-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66ff1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66ff1-120">Requirements</span></span>  
 <span data-ttu-id="66ff1-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66ff1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66ff1-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66ff1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66ff1-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66ff1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66ff1-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66ff1-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ff1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="66ff1-125">See Also</span></span>  
 [<span data-ttu-id="66ff1-126">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="66ff1-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="66ff1-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="66ff1-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
