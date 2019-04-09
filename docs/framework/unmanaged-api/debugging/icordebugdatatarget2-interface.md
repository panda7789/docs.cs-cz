---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a74ba2b5c1dc2340d20a793bcf3b14e2af234b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149614"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="c6bab-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c6bab-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="c6bab-103">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6bab-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6bab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c6bab-104">Methods</span></span>  
  
|<span data-ttu-id="c6bab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-105">Method</span></span>|<span data-ttu-id="c6bab-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c6bab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6bab-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="c6bab-108">Vytvoří nový unwinder zásobníku, který se spustí uvolnění z počáteční kontextu, (což není nutně listu vlákno).</span><span class="sxs-lookup"><span data-stu-id="c6bab-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="c6bab-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="c6bab-110">Vrátí seznam hodnot aktivní vlákno ID.</span><span class="sxs-lookup"><span data-stu-id="c6bab-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="c6bab-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="c6bab-112">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="c6bab-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="c6bab-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="c6bab-114">Vrátí cestu modulu z modulu Základní adresa.</span><span class="sxs-lookup"><span data-stu-id="c6bab-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="c6bab-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="c6bab-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="c6bab-116">Vrátí poskytovatel symbolů pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="c6bab-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6bab-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6bab-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6bab-118">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6bab-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c6bab-119">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6bab-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6bab-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6bab-120">Requirements</span></span>  
 <span data-ttu-id="c6bab-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6bab-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6bab-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6bab-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6bab-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6bab-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c6bab-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c6bab-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6bab-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6bab-125">See also</span></span>

- [<span data-ttu-id="c6bab-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6bab-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c6bab-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="c6bab-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
