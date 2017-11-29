---
title: "ICorDebug – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a29133252277cbf614a1916af6fa4c6905a920
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="e75d3-102">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e75d3-102">ICorDebug Interface</span></span>
<span data-ttu-id="e75d3-103">Poskytuje metody, které umožňují vývojářům ladit aplikace v běžné prostředí runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="e75d3-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e75d3-104">Ladění ve smíšeném režimu (spravovaná a nativní kód) není podporována v systému Windows 95, Windows 98 nebo Windows ME nebo na jiný x86 platformy (například IA64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="e75d3-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e75d3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e75d3-105">Methods</span></span>  
  
|<span data-ttu-id="e75d3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-106">Method</span></span>|<span data-ttu-id="e75d3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e75d3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e75d3-108">Canlaunchorattach – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="e75d3-109">Určuje, zda je možné v rámci aktuální konfiguraci počítače a prostředí runtime spouštění nového procesu nebo připojení do daného procesu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="e75d3-110">CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="e75d3-111">Spustí se proces a jeho primární vlákno pod kontrolou ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="e75d3-112">DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="e75d3-113">Připojí ladicí program pro existující proces.</span><span class="sxs-lookup"><span data-stu-id="e75d3-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="e75d3-114">Enumerateprocesses – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="e75d3-115">Získá enumerátor pro procesy, které se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="e75d3-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="e75d3-116">Getprocess – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="e75d3-117">Vrátí objekt "ICorDebugProcess" s ID daného procesu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="e75d3-118">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="e75d3-119">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="e75d3-120">Setmanagedhandler – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="e75d3-121">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="e75d3-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="e75d3-122">Setunmanagedhandler – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="e75d3-123">Určuje objekt obslužné rutiny události pro události se nespravované.</span><span class="sxs-lookup"><span data-stu-id="e75d3-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="e75d3-124">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="e75d3-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="e75d3-125">Ukončí `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e75d3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e75d3-126">Remarks</span></span>  
 <span data-ttu-id="e75d3-127">`ICorDebug`představuje smyčky zpracování událostí pro proces ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="e75d3-128">Ladicí program musí počkat [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání ze všech procesů laděné před uvolněním toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e75d3-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="e75d3-129">`ICorDebug` Objektu je objekt počáteční řídit všechny další spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="e75d3-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="e75d3-130">V rozhraní .NET Framework verze 1.0 a 1.1, byl tento objekt `CoClass` objekt vytvořený z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e75d3-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="e75d3-131">V rozhraní .NET Framework verze 2.0, tento objekt je už `CoClass` objektu.</span><span class="sxs-lookup"><span data-stu-id="e75d3-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="e75d3-132">Musí být vytvořen pomocí [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkci, která je zvýšení povědomí pro verzi.</span><span class="sxs-lookup"><span data-stu-id="e75d3-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="e75d3-133">Tato nová funkce vytváření umožňuje klientům získat na konkrétní implementace `ICorDebug`, což emuluje také na konkrétní verzi rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e75d3-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e75d3-134">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e75d3-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e75d3-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e75d3-135">Requirements</span></span>  
 <span data-ttu-id="e75d3-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e75d3-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e75d3-137">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e75d3-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e75d3-138">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e75d3-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e75d3-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e75d3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75d3-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="e75d3-140">See Also</span></span>  
 [<span data-ttu-id="e75d3-141">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e75d3-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
