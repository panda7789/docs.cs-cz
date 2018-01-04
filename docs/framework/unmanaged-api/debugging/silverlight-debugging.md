---
title: "Ladění aplikací Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6869e58ca47b7b55a5b988e0f6ae4a224f0f35a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="silverlight-debugging"></a><span data-ttu-id="0990b-102">Ladění aplikací Silverlight</span><span class="sxs-lookup"><span data-stu-id="0990b-102">Silverlight Debugging</span></span>
<span data-ttu-id="0990b-103">Témata v této části popisují prostředí a rozhraní, které modul CLR (CLR) poskytuje pro podporu ladění aplikace založená na technologii Silverlight, které běží na operačním systému Windows, nebo na platformě Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0990b-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0990b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0990b-104">In This Section</span></span>  
 [<span data-ttu-id="0990b-105">EnumerateCLRs – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="0990b-106">Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.</span><span class="sxs-lookup"><span data-stu-id="0990b-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="0990b-107">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="0990b-108">Zavře platný události pokračovat spuštění CLR umístěný v pole vrácené obslužné rutiny [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězec.</span><span class="sxs-lookup"><span data-stu-id="0990b-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="0990b-109">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="0990b-110">Vytvoří připojení ke vzdálené cíle pro výčet proces a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0990b-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0990b-111">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="0990b-112">Vytvoří rozhraní ladicí program, který poskytuje funkci pro vytvoření instance spravované ladicí relace na vzdálený proces.</span><span class="sxs-lookup"><span data-stu-id="0990b-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="0990b-113">CreateVersionStringFromModule – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="0990b-114">Vytvoří řetězec verze z cesty CLR v Cílový proces.</span><span class="sxs-lookup"><span data-stu-id="0990b-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="0990b-115">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="0990b-116">Přijímá řetězec verze CLR vrácená z [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)fungovat a vrátí odpovídající rozhraní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0990b-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="0990b-117">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="0990b-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="0990b-118">Představuje proces, který běží na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="0990b-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="0990b-119">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="0990b-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="0990b-120">Reprezentuje instanci CLR, který je načten do procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="0990b-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="0990b-121">GetStartupNotificationEvent – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="0990b-122">Vytvoří nebo otevře popisovač události, který se bude dát signál při jakékoli modul common language runtime (CLR), se načítá v zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="0990b-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="0990b-123">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0990b-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="0990b-124">Vytvoří připojení ke vzdálené cíle pro výčet proces a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0990b-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0990b-125">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="0990b-126">Inicializuje správce přenosu pro připojení k vzdálené cíle pro výčet proces a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0990b-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0990b-127">ShutdownDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="0990b-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="0990b-128">Správce přenosu pro připojení k vzdálené cílový počítač vypne.</span><span class="sxs-lookup"><span data-stu-id="0990b-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0990b-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0990b-129">See Also</span></span>  
 [<span data-ttu-id="0990b-130">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="0990b-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="0990b-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0990b-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0990b-132">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="0990b-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="0990b-133">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0990b-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="0990b-134">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="0990b-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
