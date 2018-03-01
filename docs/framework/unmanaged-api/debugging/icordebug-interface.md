---
title: "ICorDebug – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ed0b3a8b42157f6a4fcbc6b4a05a416da736147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="06898-102">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06898-102">ICorDebug Interface</span></span>
<span data-ttu-id="06898-103">Poskytuje metody, které umožňují vývojářům ladit aplikace v běžné prostředí runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="06898-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06898-104">Ladění ve smíšeném režimu (spravovaná a nativní kód) není podporována v systému Windows 95, Windows 98 nebo Windows ME nebo na jiný x86 platformy (například IA64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="06898-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06898-105">Metody</span><span class="sxs-lookup"><span data-stu-id="06898-105">Methods</span></span>  
  
|<span data-ttu-id="06898-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="06898-106">Method</span></span>|<span data-ttu-id="06898-107">Popis</span><span class="sxs-lookup"><span data-stu-id="06898-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06898-108">CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="06898-109">Určuje, zda je možné v rámci aktuální konfiguraci počítače a prostředí runtime spouštění nového procesu nebo připojení do daného procesu.</span><span class="sxs-lookup"><span data-stu-id="06898-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="06898-110">CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="06898-111">Spustí se proces a jeho primární vlákno pod kontrolou ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="06898-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="06898-112">DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="06898-113">Připojí ladicí program pro existující proces.</span><span class="sxs-lookup"><span data-stu-id="06898-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="06898-114">EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="06898-115">Získá enumerátor pro procesy, které se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="06898-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="06898-116">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="06898-117">Vrátí objekt "ICorDebugProcess" s ID daného procesu.</span><span class="sxs-lookup"><span data-stu-id="06898-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="06898-118">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="06898-119">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="06898-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="06898-120">SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="06898-121">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="06898-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="06898-122">SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="06898-123">Určuje objekt obslužné rutiny události pro události se nespravované.</span><span class="sxs-lookup"><span data-stu-id="06898-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="06898-124">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="06898-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="06898-125">Ukončí `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="06898-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06898-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06898-126">Remarks</span></span>  
 <span data-ttu-id="06898-127">`ICorDebug`představuje smyčky zpracování událostí pro proces ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="06898-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="06898-128">Ladicí program musí počkat [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání ze všech procesů laděné před uvolněním toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06898-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="06898-129">`ICorDebug` Objektu je objekt počáteční řídit všechny další spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="06898-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="06898-130">V rozhraní .NET Framework verze 1.0 a 1.1, byl tento objekt `CoClass` objekt vytvořený z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="06898-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="06898-131">V rozhraní .NET Framework verze 2.0, tento objekt je už `CoClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="06898-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="06898-132">Musí být vytvořen pomocí [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkci, která je zvýšení povědomí pro verzi.</span><span class="sxs-lookup"><span data-stu-id="06898-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="06898-133">Tato nová funkce vytváření umožňuje klientům získat na konkrétní implementace `ICorDebug`, což emuluje také na konkrétní verzi rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="06898-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06898-134">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="06898-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06898-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06898-135">Requirements</span></span>  
 <span data-ttu-id="06898-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06898-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06898-137">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06898-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06898-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06898-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06898-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06898-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06898-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="06898-140">See Also</span></span>  
 [<span data-ttu-id="06898-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="06898-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
