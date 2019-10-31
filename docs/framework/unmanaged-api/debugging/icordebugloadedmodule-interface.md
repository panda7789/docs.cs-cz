---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9fe36497844b9c33cefcf8c63711941196847525
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122607"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="aa166-102">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="aa166-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="aa166-103">Poskytuje informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="aa166-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa166-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aa166-104">Methods</span></span>  
  
|<span data-ttu-id="aa166-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa166-105">Method</span></span>|<span data-ttu-id="aa166-106">Popis</span><span class="sxs-lookup"><span data-stu-id="aa166-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa166-107">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="aa166-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="aa166-108">Načte základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="aa166-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="aa166-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="aa166-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="aa166-110">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="aa166-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="aa166-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="aa166-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="aa166-112">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="aa166-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa166-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa166-113">Remarks</span></span>  
 <span data-ttu-id="aa166-114">Rozhraní `ICorDebugLoadedModule` je implementováno pomocí ladicího programu a používá rozhraní ladění CLR k získání informací o načteném modulu z ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="aa166-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa166-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aa166-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="aa166-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="aa166-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa166-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa166-117">Requirements</span></span>  
 <span data-ttu-id="aa166-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa166-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa166-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa166-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa166-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aa166-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa166-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa166-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa166-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa166-122">See also</span></span>

- [<span data-ttu-id="aa166-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aa166-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aa166-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="aa166-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
