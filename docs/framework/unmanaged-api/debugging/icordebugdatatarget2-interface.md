---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 472ea0b3d54c025cdd69957765ad2663c7288b15
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783562"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="4b1dc-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="4b1dc-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="4b1dc-103">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4b1dc-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b1dc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4b1dc-104">Methods</span></span>  
  
|<span data-ttu-id="4b1dc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-105">Method</span></span>|<span data-ttu-id="4b1dc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4b1dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b1dc-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-107">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="4b1dc-108">Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).</span><span class="sxs-lookup"><span data-stu-id="4b1dc-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="4b1dc-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-109">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="4b1dc-110">Vrátí seznam identifikátorů aktivních vláken.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="4b1dc-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-111">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="4b1dc-112">Vrátí základní adresu modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="4b1dc-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-113">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="4b1dc-114">Vrátí cestu modulu ze základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="4b1dc-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1dc-115">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="4b1dc-116">Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b1dc-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b1dc-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b1dc-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4b1dc-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="4b1dc-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b1dc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b1dc-120">Requirements</span></span>  
 <span data-ttu-id="4b1dc-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b1dc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b1dc-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b1dc-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b1dc-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b1dc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b1dc-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b1dc-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1dc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b1dc-125">See also</span></span>

- [<span data-ttu-id="4b1dc-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4b1dc-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4b1dc-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="4b1dc-127">Debugging</span></span>](index.md)
