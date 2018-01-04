---
title: "invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 395601c6aaff39bf2acb01ae36d306e57566aa4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="48cde-102">invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="48cde-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="48cde-103">`invalidOverlappedToPinvoke` Pomocník spravovaného ladění (MDA) se aktivuje, když překrytý ukazatel, jež nebyla vytvořena v haldě kolekce paměti předána ke konkrétním funkcím Win32.</span><span class="sxs-lookup"><span data-stu-id="48cde-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48cde-104">Ve výchozím nastavení tento MDA je aktivována, jenom Pokud platformou vyvolat volání je definována v kódu a ladicí program hlásí stav JustMyCode každé metody.</span><span class="sxs-lookup"><span data-stu-id="48cde-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="48cde-105">Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez přípony) nebudou aktivovat tuto (mda).</span><span class="sxs-lookup"><span data-stu-id="48cde-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="48cde-106">Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně settting `justMyCode="false"` v. soubor mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="48cde-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="48cde-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="48cde-107">Symptoms</span></span>  
 <span data-ttu-id="48cde-108">Poškození haldy unexplainable nebo dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="48cde-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="48cde-109">příčina</span><span class="sxs-lookup"><span data-stu-id="48cde-109">Cause</span></span>  
 <span data-ttu-id="48cde-110">Překryté ukazatele, jež nebyla vytvořena v haldě kolekce paměti se předají funkcím konkrétní operační systém.</span><span class="sxs-lookup"><span data-stu-id="48cde-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="48cde-111">Následující tabulka uvádí funkce, že tento MDA sleduje.</span><span class="sxs-lookup"><span data-stu-id="48cde-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="48cde-112">Modul</span><span class="sxs-lookup"><span data-stu-id="48cde-112">Module</span></span>|<span data-ttu-id="48cde-113">Funkce</span><span class="sxs-lookup"><span data-stu-id="48cde-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="48cde-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="48cde-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="48cde-116">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="48cde-117">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="48cde-118">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="48cde-119">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="48cde-120">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="48cde-121">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="48cde-122">Mswsock.dll –</span><span class="sxs-lookup"><span data-stu-id="48cde-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="48cde-123">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="48cde-124">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="48cde-125">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="48cde-126">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="48cde-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="48cde-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="48cde-128">Tato podmínka, protože je vysoká potenciální poškození haldy <xref:System.AppDomain> provádění volání může mít za následek uvolnění.</span><span class="sxs-lookup"><span data-stu-id="48cde-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="48cde-129">Pokud <xref:System.AppDomain> uvolní, kódu aplikace bude buď volné paměti pro překrytý ukazatel způsobuje poškození při dokončení operace nebo kód bude úniku paměť, způsobuje problémy později.</span><span class="sxs-lookup"><span data-stu-id="48cde-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="48cde-130">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="48cde-130">Resolution</span></span>  
 <span data-ttu-id="48cde-131">Použijte <xref:System.Threading.Overlapped> objektu, volání <xref:System.Threading.Overlapped.Pack%2A> metodu za účelem získání <xref:System.Threading.NativeOverlapped> struktura, která může být předaný funkci.</span><span class="sxs-lookup"><span data-stu-id="48cde-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="48cde-132">Pokud <xref:System.AppDomain> uvolní, modul CLR čeká na dokončení asynchronní operace před uvolnění ukazatele.</span><span class="sxs-lookup"><span data-stu-id="48cde-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="48cde-133">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="48cde-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="48cde-134">Tato MDA nemělo žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="48cde-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="48cde-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="48cde-135">Output</span></span>  
 <span data-ttu-id="48cde-136">Následuje příklad výstupu z této (mda).</span><span class="sxs-lookup"><span data-stu-id="48cde-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="48cde-137">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="48cde-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48cde-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="48cde-138">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="48cde-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="48cde-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="48cde-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="48cde-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
