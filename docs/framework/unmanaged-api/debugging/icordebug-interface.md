---
title: ICorDebug – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: ee6bcbc9f3377735ed289d52afddb6efa755b16d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134078"
---
# <a name="icordebug-interface"></a><span data-ttu-id="c11eb-102">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c11eb-102">ICorDebug Interface</span></span>
<span data-ttu-id="c11eb-103">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c11eb-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c11eb-104">Ladění ve smíšeném režimu (spravovaný a nativní kód) není podporováno ve Windows 95, Windows 98 nebo Windows Millennium Edition ani na platformách jiných než x86 (například IA64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="c11eb-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c11eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c11eb-105">Methods</span></span>  
  
|<span data-ttu-id="c11eb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-106">Method</span></span>|<span data-ttu-id="c11eb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c11eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c11eb-108">CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="c11eb-109">Určuje, zda je možné v kontextu aktuálního počítače a konfigurace modulu runtime spustit nový proces nebo připojení k danému procesu.</span><span class="sxs-lookup"><span data-stu-id="c11eb-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="c11eb-110">CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="c11eb-111">Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c11eb-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="c11eb-112">DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="c11eb-113">Připojí ladicí program k existujícímu procesu.</span><span class="sxs-lookup"><span data-stu-id="c11eb-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="c11eb-114">EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="c11eb-115">Získá enumerátor pro procesy, které jsou laděny.</span><span class="sxs-lookup"><span data-stu-id="c11eb-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="c11eb-116">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="c11eb-117">Vrátí objekt "ICorDebugProcess" s daným ID procesu.</span><span class="sxs-lookup"><span data-stu-id="c11eb-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="c11eb-118">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="c11eb-119">Inicializuje objekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c11eb-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="c11eb-120">SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="c11eb-121">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="c11eb-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="c11eb-122">SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="c11eb-123">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="c11eb-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="c11eb-124">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="c11eb-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="c11eb-125">Ukončí objekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c11eb-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c11eb-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c11eb-126">Remarks</span></span>  
 <span data-ttu-id="c11eb-127">`ICorDebug` představuje smyčku zpracování událostí pro proces ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c11eb-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="c11eb-128">Ladicí program musí počkat na zpětné volání [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ze všech procesů, které jsou laděny před uvolněním tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c11eb-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="c11eb-129">Objekt `ICorDebug` je počáteční objekt pro řízení všech dalších spravovaných ladění.</span><span class="sxs-lookup"><span data-stu-id="c11eb-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="c11eb-130">V .NET Framework verzích 1,0 a 1,1 byl tento objekt objektem `CoClass` vytvořeným z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c11eb-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="c11eb-131">V .NET Framework verze 2,0 Tento objekt již není objektem `CoClass`.</span><span class="sxs-lookup"><span data-stu-id="c11eb-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="c11eb-132">Musí být vytvořen funkcí [CreateDebuggingInterfaceFromVersion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , což je více zohledňuje verze.</span><span class="sxs-lookup"><span data-stu-id="c11eb-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="c11eb-133">Tato nová funkce vytváření umožňuje klientům získat konkrétní implementaci `ICorDebug`, která také emuluje konkrétní verzi rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c11eb-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c11eb-134">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c11eb-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c11eb-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c11eb-135">Requirements</span></span>  
 <span data-ttu-id="c11eb-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c11eb-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c11eb-137">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c11eb-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c11eb-138">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c11eb-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c11eb-139">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c11eb-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11eb-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c11eb-140">See also</span></span>

- [<span data-ttu-id="c11eb-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c11eb-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
