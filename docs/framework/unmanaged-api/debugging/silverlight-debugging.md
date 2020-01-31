---
title: Ladění aplikací Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790315"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="c7999-102">Ladění aplikací Silverlight</span><span class="sxs-lookup"><span data-stu-id="c7999-102">Silverlight Debugging</span></span>
<span data-ttu-id="c7999-103">Témata v této části popisují prostředí a rozhraní, které modul CLR (Common Language Runtime) poskytuje pro podporu ladění aplikací založených na programu Silverlight, které jsou spuštěny v operačním systému Windows nebo na platformě Macintosh.</span><span class="sxs-lookup"><span data-stu-id="c7999-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7999-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c7999-104">In This Section</span></span>  
 [<span data-ttu-id="c7999-105">EnumerateCLRs – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="c7999-106">Poskytuje mechanismus pro vytváření výčtu CLRs v procesu.</span><span class="sxs-lookup"><span data-stu-id="c7999-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="c7999-107">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="c7999-108">Ukončí všechny platné události před spuštěním CLR, které se nacházejí v poli popisovačů vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md), a uvolní paměť pro pole popisovače a cestu k řetězci.</span><span class="sxs-lookup"><span data-stu-id="c7999-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="c7999-109">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="c7999-110">Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.</span><span class="sxs-lookup"><span data-stu-id="c7999-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c7999-111">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="c7999-112">Vytvoří rozhraní ladicího programu, které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.</span><span class="sxs-lookup"><span data-stu-id="c7999-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="c7999-113">CreateVersionStringFromModule – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="c7999-114">Vytvoří řetězec verze z cesty CLR v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="c7999-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="c7999-115">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="c7999-116">Přijímá řetězec verze CLR vrácený funkcí [CreateVersionStringFromModule – funkce](createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c7999-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="c7999-117">CoreClrDebugProcInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c7999-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="c7999-118">Představuje proces, který je spuštěn ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="c7999-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="c7999-119">CoreClrDebugRuntimeInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c7999-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="c7999-120">Představuje instanci CLR, která je načtena v procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="c7999-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="c7999-121">GetStartupNotificationEvent – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="c7999-122">Vytvoří nebo otevře obslužnou rutinu události, která bude signalizována jakýmkoli modulem CLR (Common Language Runtime), který se načítá v zadaném cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="c7999-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="c7999-123">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7999-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="c7999-124">Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.</span><span class="sxs-lookup"><span data-stu-id="c7999-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c7999-125">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="c7999-126">Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.</span><span class="sxs-lookup"><span data-stu-id="c7999-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c7999-127">ShutdownDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="c7999-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="c7999-128">Ukončí Správce přenosů pro připojení ke vzdálenému cílovému počítači.</span><span class="sxs-lookup"><span data-stu-id="c7999-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7999-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7999-129">See also</span></span>

- [<span data-ttu-id="c7999-130">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7999-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="c7999-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7999-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c7999-132">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7999-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="c7999-133">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7999-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c7999-134">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7999-134">Debugging Structures</span></span>](debugging-structures.md)
