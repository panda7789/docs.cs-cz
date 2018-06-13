---
title: invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7240692e35c97f3efbc33ca27a0221da1d250149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386854"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="f2812-102">invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f2812-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="f2812-103">`invalidOverlappedToPinvoke` Pomocník spravovaného ladění (MDA) se aktivuje, když překrytý ukazatel, jež nebyla vytvořena v haldě kolekce paměti předána ke konkrétním funkcím Win32.</span><span class="sxs-lookup"><span data-stu-id="f2812-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2812-104">Ve výchozím nastavení tento MDA je aktivována, jenom Pokud platformou vyvolat volání je definována v kódu a ladicí program hlásí stav JustMyCode každé metody.</span><span class="sxs-lookup"><span data-stu-id="f2812-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="f2812-105">Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez přípony) nebudou aktivovat tuto (mda).</span><span class="sxs-lookup"><span data-stu-id="f2812-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="f2812-106">Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně settting `justMyCode="false"` v. soubor mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="f2812-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f2812-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f2812-107">Symptoms</span></span>  
 <span data-ttu-id="f2812-108">Poškození haldy unexplainable nebo dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="f2812-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f2812-109">příčina</span><span class="sxs-lookup"><span data-stu-id="f2812-109">Cause</span></span>  
 <span data-ttu-id="f2812-110">Překryté ukazatele, jež nebyla vytvořena v haldě kolekce paměti se předají funkcím konkrétní operační systém.</span><span class="sxs-lookup"><span data-stu-id="f2812-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="f2812-111">Následující tabulka uvádí funkce, že tento MDA sleduje.</span><span class="sxs-lookup"><span data-stu-id="f2812-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="f2812-112">Modul</span><span class="sxs-lookup"><span data-stu-id="f2812-112">Module</span></span>|<span data-ttu-id="f2812-113">Funkce</span><span class="sxs-lookup"><span data-stu-id="f2812-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="f2812-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="f2812-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="f2812-116">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="f2812-117">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="f2812-118">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="f2812-119">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="f2812-120">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="f2812-121">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="f2812-122">Mswsock.dll –</span><span class="sxs-lookup"><span data-stu-id="f2812-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="f2812-123">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="f2812-124">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="f2812-125">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="f2812-126">Ws2_32.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="f2812-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="f2812-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="f2812-128">Tato podmínka, protože je vysoká potenciální poškození haldy <xref:System.AppDomain> provádění volání může mít za následek uvolnění.</span><span class="sxs-lookup"><span data-stu-id="f2812-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="f2812-129">Pokud <xref:System.AppDomain> uvolní, kódu aplikace bude buď volné paměti pro překrytý ukazatel způsobuje poškození při dokončení operace nebo kód bude úniku paměť, způsobuje problémy později.</span><span class="sxs-lookup"><span data-stu-id="f2812-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f2812-130">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="f2812-130">Resolution</span></span>  
 <span data-ttu-id="f2812-131">Použijte <xref:System.Threading.Overlapped> objektu, volání <xref:System.Threading.Overlapped.Pack%2A> metodu za účelem získání <xref:System.Threading.NativeOverlapped> struktura, která může být předaný funkci.</span><span class="sxs-lookup"><span data-stu-id="f2812-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="f2812-132">Pokud <xref:System.AppDomain> uvolní, modul CLR čeká na dokončení asynchronní operace před uvolnění ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f2812-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f2812-133">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="f2812-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="f2812-134">Tato MDA nemělo žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f2812-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f2812-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="f2812-135">Output</span></span>  
 <span data-ttu-id="f2812-136">Následuje příklad výstupu z této (mda).</span><span class="sxs-lookup"><span data-stu-id="f2812-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="f2812-137">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f2812-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2812-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2812-138">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f2812-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f2812-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f2812-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f2812-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
