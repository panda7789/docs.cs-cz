---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200750"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="19345-102">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="19345-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="19345-103">Poskytuje informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="19345-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19345-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19345-104">Methods</span></span>  
  
|<span data-ttu-id="19345-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19345-105">Method</span></span>|<span data-ttu-id="19345-106">Popis</span><span class="sxs-lookup"><span data-stu-id="19345-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19345-107">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="19345-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="19345-108">Získá základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="19345-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="19345-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="19345-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="19345-110">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="19345-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="19345-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="19345-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="19345-112">Získá velikost v bajtech načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="19345-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19345-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19345-113">Remarks</span></span>  
 <span data-ttu-id="19345-114">`ICorDebugLoadedModule` Rozhraní je implementováno ladicím programem a používá modul CLR rozhraní pro ladění a získat informace o modulu načteny z ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="19345-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19345-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="19345-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="19345-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="19345-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19345-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19345-117">Requirements</span></span>  
 <span data-ttu-id="19345-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19345-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19345-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19345-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19345-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19345-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19345-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19345-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19345-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19345-122">See also</span></span>

- [<span data-ttu-id="19345-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19345-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="19345-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="19345-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
