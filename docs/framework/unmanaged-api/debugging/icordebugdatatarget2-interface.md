---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 1c598d23cac77e50cf302e6936b88b5eb6e558c2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976431"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="c2eb2-102">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c2eb2-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="c2eb2-103">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2eb2-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2eb2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2eb2-104">Methods</span></span>  
  
|<span data-ttu-id="c2eb2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-105">Method</span></span>|<span data-ttu-id="c2eb2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2eb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2eb2-107">CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-107">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="c2eb2-108">Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).</span><span class="sxs-lookup"><span data-stu-id="c2eb2-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="c2eb2-109">EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-109">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="c2eb2-110">Vrátí seznam identifikátorů aktivních vláken.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="c2eb2-111">GetImageFromPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-111">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="c2eb2-112">Vrátí základní adresu modulu a velikost z adresy v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="c2eb2-113">GetImageLocation – metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-113">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="c2eb2-114">Vrátí cestu modulu ze základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="c2eb2-115">GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="c2eb2-115">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="c2eb2-116">Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2eb2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2eb2-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2eb2-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c2eb2-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="c2eb2-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2eb2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2eb2-120">Requirements</span></span>  
 <span data-ttu-id="c2eb2-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2eb2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2eb2-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2eb2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2eb2-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2eb2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2eb2-124">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2eb2-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2eb2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2eb2-125">See also</span></span>

- [<span data-ttu-id="c2eb2-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2eb2-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c2eb2-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="c2eb2-127">Debugging</span></span>](index.md)
