---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07d6dcc1873e24f84f97c877e8198c27eceef0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420788"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="0d6fb-102">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="0d6fb-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="0d6fb-103">Poskytuje informace o načíst modul.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d6fb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0d6fb-104">Methods</span></span>  
  
|<span data-ttu-id="0d6fb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0d6fb-105">Method</span></span>|<span data-ttu-id="0d6fb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0d6fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d6fb-107">GetBaseAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6fb-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="0d6fb-108">Získá základní adresu načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="0d6fb-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6fb-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="0d6fb-110">Získá název načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="0d6fb-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6fb-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="0d6fb-112">Získá velikost v bajtech načíst modul.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d6fb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d6fb-113">Remarks</span></span>  
 <span data-ttu-id="0d6fb-114">`ICorDebugLoadedModule` Rozhraní je implementováno modulem ladicí program a je používána CLR ladění v rozhraní pro získání informací o načíst modul z ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d6fb-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0d6fb-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0d6fb-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d6fb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d6fb-117">Requirements</span></span>  
 <span data-ttu-id="0d6fb-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6fb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6fb-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d6fb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d6fb-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d6fb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d6fb-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6fb-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6fb-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d6fb-122">See Also</span></span>  
 [<span data-ttu-id="0d6fb-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0d6fb-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0d6fb-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="0d6fb-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
