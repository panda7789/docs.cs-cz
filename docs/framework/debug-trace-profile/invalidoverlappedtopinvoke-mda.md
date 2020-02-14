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
ms.openlocfilehash: 1f557cc370d5c6121b0ad9a4528bd75dcb70a93c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216278"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="64a5a-102">invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="64a5a-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="64a5a-103">Pokud překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím Win32, je aktivován Pomocník pro `invalidOverlappedToPinvoke` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="64a5a-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64a5a-104">Ve výchozím nastavení je tento MDA aktivován pouze v případě, že je ve vašem kódu definováno volání metody Invoke a ladicí program ohlásí stav JustMyCode pro každou metodu.</span><span class="sxs-lookup"><span data-stu-id="64a5a-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="64a5a-105">Ladicí program, který nerozumí JustMyCode (například MDbg. exe bez rozšíření), neaktivuje Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="64a5a-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="64a5a-106">Tento MDA lze povolit pro tyto ladicí programy pomocí konfiguračního souboru a explicitně nastavit `justMyCode="false"` v souboru. MDA. config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="64a5a-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="64a5a-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="64a5a-107">Symptoms</span></span>  
 <span data-ttu-id="64a5a-108">Selhání nebo nejasná poškození haldy.</span><span class="sxs-lookup"><span data-stu-id="64a5a-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="64a5a-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="64a5a-109">Cause</span></span>  
 <span data-ttu-id="64a5a-110">Překrývající ukazatel, který nebyl vytvořen na haldě uvolňování paměti, je předán konkrétním funkcím operačního systému.</span><span class="sxs-lookup"><span data-stu-id="64a5a-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="64a5a-111">V následující tabulce jsou uvedeny funkce, které tento MDA sleduje.</span><span class="sxs-lookup"><span data-stu-id="64a5a-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="64a5a-112">Modul</span><span class="sxs-lookup"><span data-stu-id="64a5a-112">Module</span></span>|<span data-ttu-id="64a5a-113">Funkce</span><span class="sxs-lookup"><span data-stu-id="64a5a-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="64a5a-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="64a5a-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="64a5a-116">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="64a5a-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="64a5a-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="64a5a-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="64a5a-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="64a5a-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="64a5a-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="64a5a-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="64a5a-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="64a5a-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="64a5a-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="64a5a-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="64a5a-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="64a5a-128">Potenciál pro poškození haldy je pro tento stav vysoký, protože <xref:System.AppDomain> volání může být uvolněno.</span><span class="sxs-lookup"><span data-stu-id="64a5a-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="64a5a-129">Pokud se <xref:System.AppDomain> uvolní, kód aplikace buď uvolní paměť pro překrývající ukazatel, což způsobí poškození po dokončení operace, nebo kód vrátí paměť, což způsobí obtíže později.</span><span class="sxs-lookup"><span data-stu-id="64a5a-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="64a5a-130">Řešení</span><span class="sxs-lookup"><span data-stu-id="64a5a-130">Resolution</span></span>  
 <span data-ttu-id="64a5a-131">Použijte objekt <xref:System.Threading.Overlapped>, voláním metody <xref:System.Threading.Overlapped.Pack%2A> získáte strukturu <xref:System.Threading.NativeOverlapped>, která může být předána funkci.</span><span class="sxs-lookup"><span data-stu-id="64a5a-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="64a5a-132">Pokud se <xref:System.AppDomain> uvolní, modul CLR počká, dokud se asynchronní operace nedokončí před uvolněním ukazatele.</span><span class="sxs-lookup"><span data-stu-id="64a5a-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="64a5a-133">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="64a5a-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="64a5a-134">Tento MDA neměl žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="64a5a-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="64a5a-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="64a5a-135">Output</span></span>  
 <span data-ttu-id="64a5a-136">Následuje příklad výstupu z tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="64a5a-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="64a5a-137">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="64a5a-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64a5a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="64a5a-138">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="64a5a-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="64a5a-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="64a5a-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="64a5a-140">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
