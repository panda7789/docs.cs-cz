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
ms.openlocfilehash: 66b50bad0e8d2622922da96c213643ac3be83a9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895362"
---
# <a name="icordebug-interface"></a><span data-ttu-id="2bb85-102">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bb85-102">ICorDebug Interface</span></span>
<span data-ttu-id="2bb85-103">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="2bb85-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb85-104">Ladění ve smíšeném režimu (spravovaný a nativní kód) není podporováno ve Windows 95, Windows 98 nebo Windows Millennium Edition ani na platformách jiných než x86 (například IA64 a AMD64).</span><span class="sxs-lookup"><span data-stu-id="2bb85-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bb85-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2bb85-105">Methods</span></span>  
  
|<span data-ttu-id="2bb85-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-106">Method</span></span>|<span data-ttu-id="2bb85-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2bb85-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bb85-108">CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-108">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="2bb85-109">Určuje, zda je možné v kontextu aktuálního počítače a konfigurace modulu runtime spustit nový proces nebo připojení k danému procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="2bb85-110">CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-110">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="2bb85-111">Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="2bb85-112">DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-112">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="2bb85-113">Připojí ladicí program k existujícímu procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="2bb85-114">EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-114">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="2bb85-115">Získá enumerátor pro procesy, které jsou laděny.</span><span class="sxs-lookup"><span data-stu-id="2bb85-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="2bb85-116">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-116">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="2bb85-117">Vrátí objekt "ICorDebugProcess" s daným ID procesu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="2bb85-118">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-118">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="2bb85-119">Inicializuje `ICorDebug` objekt.</span><span class="sxs-lookup"><span data-stu-id="2bb85-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="2bb85-120">SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-120">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="2bb85-121">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="2bb85-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="2bb85-122">SetUnmanagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-122">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="2bb85-123">Určuje objekt obslužné rutiny události pro nespravované události.</span><span class="sxs-lookup"><span data-stu-id="2bb85-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="2bb85-124">Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="2bb85-124">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="2bb85-125">Ukončí `ICorDebug` objekt.</span><span class="sxs-lookup"><span data-stu-id="2bb85-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb85-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bb85-126">Remarks</span></span>  
 <span data-ttu-id="2bb85-127">`ICorDebug`představuje smyčku zpracování událostí pro proces ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2bb85-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="2bb85-128">Ladicí program musí počkat na zpětné volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) ze všech procesů, které jsou laděny před uvolněním tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2bb85-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="2bb85-129">`ICorDebug` Objekt je počáteční objekt pro řízení všech dalších spravovaných ladění.</span><span class="sxs-lookup"><span data-stu-id="2bb85-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="2bb85-130">V .NET Framework verzích 1,0 a 1,1 byl tento objekt `CoClass` objekt vytvořený z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2bb85-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="2bb85-131">V .NET Framework verze 2,0 Tento objekt již není `CoClass` objektem.</span><span class="sxs-lookup"><span data-stu-id="2bb85-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="2bb85-132">Musí být vytvořen funkcí [CreateDebuggingInterfaceFromVersion –](../hosting/createdebugginginterfacefromversion-function.md) , což je více zohledňuje verze.</span><span class="sxs-lookup"><span data-stu-id="2bb85-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="2bb85-133">Tato nová funkce vytváření umožňuje klientům získat konkrétní implementaci `ICorDebug`, která také emuluje konkrétní verzi rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="2bb85-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb85-134">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2bb85-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb85-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bb85-135">Requirements</span></span>  
 <span data-ttu-id="2bb85-136">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb85-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb85-137">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2bb85-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bb85-138">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2bb85-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bb85-139">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb85-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb85-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bb85-140">See also</span></span>

- [<span data-ttu-id="2bb85-141">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bb85-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
