---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85ff64e30519e448b87c2e9ae5d2c66959d836fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412130"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="44826-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="44826-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="44826-103">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44826-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44826-104">Metody</span><span class="sxs-lookup"><span data-stu-id="44826-104">Methods</span></span>  
  
|<span data-ttu-id="44826-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="44826-105">Method</span></span>|<span data-ttu-id="44826-106">Popis</span><span class="sxs-lookup"><span data-stu-id="44826-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44826-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="44826-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="44826-108">Vytvoří nový unwinder zásobníku, která se spouští unwinding z kontextu počáteční (který není nutně listu vlákna).</span><span class="sxs-lookup"><span data-stu-id="44826-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="44826-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="44826-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="44826-110">Vrátí seznam aktivních vláken ID.</span><span class="sxs-lookup"><span data-stu-id="44826-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="44826-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="44826-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="44826-112">Vrátí základní adresa modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="44826-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="44826-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="44826-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="44826-114">Vrátí cestu modul z modulu základní adresu.</span><span class="sxs-lookup"><span data-stu-id="44826-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="44826-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="44826-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="44826-116">Vrátí symbol zprostředkovatele pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="44826-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44826-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44826-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44826-118">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="44826-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="44826-119">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="44826-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44826-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44826-120">Requirements</span></span>  
 <span data-ttu-id="44826-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44826-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44826-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44826-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44826-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44826-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44826-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44826-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44826-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="44826-125">See Also</span></span>  
 [<span data-ttu-id="44826-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="44826-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="44826-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="44826-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
