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
ms.openlocfilehash: 7e9c7e1038591e5e8ea6f62b37ff4d02b2b6a9c5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052560"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="e34b3-102">invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="e34b3-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="e34b3-103">Pokud překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím Win32, je aktivován pomocník spravovanéholadění(MDA).`invalidOverlappedToPinvoke`</span><span class="sxs-lookup"><span data-stu-id="e34b3-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e34b3-104">Ve výchozím nastavení je tento MDA aktivován pouze v případě, že je ve vašem kódu definováno volání metody Invoke a ladicí program ohlásí stav JustMyCode pro každou metodu.</span><span class="sxs-lookup"><span data-stu-id="e34b3-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="e34b3-105">Ladicí program, který nerozumí JustMyCode (například MDbg. exe bez rozšíření), neaktivuje Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="e34b3-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="e34b3-106">Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně nastavit `justMyCode="false"` v souboru `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`. MDA. config).</span><span class="sxs-lookup"><span data-stu-id="e34b3-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e34b3-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e34b3-107">Symptoms</span></span>  
 <span data-ttu-id="e34b3-108">Selhání nebo nejasná poškození haldy.</span><span class="sxs-lookup"><span data-stu-id="e34b3-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e34b3-109">příčina</span><span class="sxs-lookup"><span data-stu-id="e34b3-109">Cause</span></span>  
 <span data-ttu-id="e34b3-110">Překrývající ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím operačního systému.</span><span class="sxs-lookup"><span data-stu-id="e34b3-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="e34b3-111">V následující tabulce jsou uvedeny funkce, které tento MDA sleduje.</span><span class="sxs-lookup"><span data-stu-id="e34b3-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="e34b3-112">Modul</span><span class="sxs-lookup"><span data-stu-id="e34b3-112">Module</span></span>|<span data-ttu-id="e34b3-113">Funkce</span><span class="sxs-lookup"><span data-stu-id="e34b3-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="e34b3-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="e34b3-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="e34b3-116">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="e34b3-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="e34b3-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="e34b3-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="e34b3-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="e34b3-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="e34b3-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="e34b3-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="e34b3-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="e34b3-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="e34b3-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="e34b3-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="e34b3-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="e34b3-128">Potenciál pro poškození haldy je pro tento stav vysoký, protože <xref:System.AppDomain> volání může být uvolněno.</span><span class="sxs-lookup"><span data-stu-id="e34b3-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="e34b3-129">Pokud se <xref:System.AppDomain> uvolní, kód aplikace buď uvolní paměť pro překrývající ukazatel, což způsobí poškození po dokončení operace, nebo kód nevrátí paměť, což způsobí obtíže později.</span><span class="sxs-lookup"><span data-stu-id="e34b3-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e34b3-130">Řešení</span><span class="sxs-lookup"><span data-stu-id="e34b3-130">Resolution</span></span>  
 <span data-ttu-id="e34b3-131">Použijte objekt, <xref:System.Threading.Overlapped.Pack%2A> voláním metody pro získání <xref:System.Threading.NativeOverlapped> struktury, která může být předána funkci. <xref:System.Threading.Overlapped></span><span class="sxs-lookup"><span data-stu-id="e34b3-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="e34b3-132">Pokud se <xref:System.AppDomain> uvolní, modul CLR počká, dokud se asynchronní operace nedokončí před uvolněním ukazatele.</span><span class="sxs-lookup"><span data-stu-id="e34b3-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e34b3-133">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="e34b3-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="e34b3-134">Tento MDA neměl žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="e34b3-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e34b3-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="e34b3-135">Output</span></span>  
 <span data-ttu-id="e34b3-136">Následuje příklad výstupu z tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="e34b3-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="e34b3-137">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="e34b3-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e34b3-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e34b3-138">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e34b3-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e34b3-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e34b3-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="e34b3-140">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
