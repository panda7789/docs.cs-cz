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
ms.workload: dotnet
ms.openlocfilehash: 2aefdb34277d2cb7ebc29ef817745b85064475d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="0767b-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="0767b-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="0767b-103">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0767b-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0767b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0767b-104">Methods</span></span>  
  
|<span data-ttu-id="0767b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-105">Method</span></span>|<span data-ttu-id="0767b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0767b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0767b-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="0767b-108">Vytvoří nový unwinder zásobníku, která se spouští unwinding z kontextu počáteční (který není nutně listu vlákna).</span><span class="sxs-lookup"><span data-stu-id="0767b-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="0767b-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="0767b-110">Vrátí seznam aktivních vláken ID.</span><span class="sxs-lookup"><span data-stu-id="0767b-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="0767b-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="0767b-112">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="0767b-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="0767b-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="0767b-114">Vrátí cestu modul z modulu základní adresu.</span><span class="sxs-lookup"><span data-stu-id="0767b-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="0767b-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="0767b-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="0767b-116">Vrátí symbol zprostředkovatele pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="0767b-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0767b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0767b-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0767b-118">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="0767b-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0767b-119">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0767b-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0767b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0767b-120">Requirements</span></span>  
 <span data-ttu-id="0767b-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0767b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0767b-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0767b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0767b-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0767b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0767b-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0767b-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0767b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="0767b-125">See Also</span></span>  
 [<span data-ttu-id="0767b-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0767b-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0767b-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="0767b-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
