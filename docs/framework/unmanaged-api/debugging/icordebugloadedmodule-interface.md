---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9da6aba61382381fc25fe70615976cd0e744ee1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910007"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="9e455-102">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="9e455-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="9e455-103">Poskytuje informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="9e455-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e455-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9e455-104">Methods</span></span>  
  
|<span data-ttu-id="9e455-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e455-105">Method</span></span>|<span data-ttu-id="9e455-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9e455-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e455-107">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9e455-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="9e455-108">Načte základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="9e455-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="9e455-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="9e455-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="9e455-110">Získá název načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="9e455-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="9e455-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9e455-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="9e455-112">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9e455-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e455-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e455-113">Remarks</span></span>  
 <span data-ttu-id="9e455-114">`ICorDebugLoadedModule` Rozhraní je implementováno pomocí ladicího programu a používá rozhraní ladění CLR k získání informací o načteném modulu z ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="9e455-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e455-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9e455-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9e455-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="9e455-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e455-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e455-117">Requirements</span></span>  
 <span data-ttu-id="9e455-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e455-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e455-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9e455-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e455-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e455-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e455-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e455-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e455-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e455-122">See also</span></span>

- [<span data-ttu-id="9e455-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9e455-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9e455-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="9e455-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
