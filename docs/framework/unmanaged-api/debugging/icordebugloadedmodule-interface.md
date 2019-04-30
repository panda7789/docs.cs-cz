---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946283"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="0fdb9-102">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="0fdb9-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="0fdb9-103">Poskytuje informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0fdb9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0fdb9-104">Methods</span></span>  
  
|<span data-ttu-id="0fdb9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0fdb9-105">Method</span></span>|<span data-ttu-id="0fdb9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0fdb9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0fdb9-107">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0fdb9-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="0fdb9-108">Získá základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="0fdb9-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="0fdb9-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="0fdb9-110">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="0fdb9-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0fdb9-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="0fdb9-112">Získá velikost v bajtech načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fdb9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fdb9-113">Remarks</span></span>  
 <span data-ttu-id="0fdb9-114">`ICorDebugLoadedModule` Rozhraní je implementováno ladicím programem a používá modul CLR rozhraní pro ladění a získat informace o modulu načteny z ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fdb9-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0fdb9-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0fdb9-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fdb9-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fdb9-117">Requirements</span></span>  
 <span data-ttu-id="0fdb9-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fdb9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fdb9-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fdb9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fdb9-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fdb9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fdb9-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fdb9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fdb9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fdb9-122">See also</span></span>

- [<span data-ttu-id="0fdb9-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0fdb9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0fdb9-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="0fdb9-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
