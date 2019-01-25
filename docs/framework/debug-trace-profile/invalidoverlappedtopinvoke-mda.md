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
ms.openlocfilehash: 4dc09f3e8cb926d31b21f0cc2a6442c7a6b8dec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714776"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="9cacc-102">invalidOverlappedToPinvoke – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="9cacc-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="9cacc-103">`invalidOverlappedToPinvoke` Pomocníka spravovaného ladění (MDA) se aktivuje, když překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti je předán konkrétním funkcím Win32.</span><span class="sxs-lookup"><span data-stu-id="9cacc-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cacc-104">Ve výchozím nastavení toto MDA aktivováno, pouze pokud platforma volání je definováno v kódu a ladicí program hlásí stav JustMyCode každé metody.</span><span class="sxs-lookup"><span data-stu-id="9cacc-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="9cacc-105">Ladicí program, který nerozumí JustMyCode (například MDbg.exe bez přípon), neaktivuje toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9cacc-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="9cacc-106">Tento MDA lze povolit pro ty ladící programy pomocí konfiguračního souboru a explicitně nastavit `justMyCode="false"` v. mda.config souboru `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="9cacc-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9cacc-107">Příznaky</span><span class="sxs-lookup"><span data-stu-id="9cacc-107">Symptoms</span></span>  
 <span data-ttu-id="9cacc-108">Selhání nebo nevysvětlitelné poškození haldy.</span><span class="sxs-lookup"><span data-stu-id="9cacc-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9cacc-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="9cacc-109">Cause</span></span>  
 <span data-ttu-id="9cacc-110">Překrytý ukazatel, který nebyl vytvořen na haldě uvolňování paměti je předán konkrétním funkcím operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9cacc-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="9cacc-111">V následující tabulce jsou uvedeny funkce, že toto MDA sleduje.</span><span class="sxs-lookup"><span data-stu-id="9cacc-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="9cacc-112">Modul</span><span class="sxs-lookup"><span data-stu-id="9cacc-112">Module</span></span>|<span data-ttu-id="9cacc-113">Funkce</span><span class="sxs-lookup"><span data-stu-id="9cacc-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="9cacc-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="9cacc-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="9cacc-116">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="9cacc-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="9cacc-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="9cacc-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="9cacc-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="9cacc-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="9cacc-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="9cacc-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="9cacc-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="9cacc-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="9cacc-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="9cacc-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="9cacc-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="9cacc-128">Potenciál pro poškození haldy je vysoký pro tuto podmínku, protože <xref:System.AppDomain> provádění volání se může uvolnit.</span><span class="sxs-lookup"><span data-stu-id="9cacc-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="9cacc-129">Pokud <xref:System.AppDomain> uvolní, kód aplikace uvolní paměť pro překrývající ukazatel, což způsobí poškození při dokončení operace nebo kód způsobí přetečení paměti, což povede k potížím později.</span><span class="sxs-lookup"><span data-stu-id="9cacc-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9cacc-130">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="9cacc-130">Resolution</span></span>  
 <span data-ttu-id="9cacc-131">Použití <xref:System.Threading.Overlapped> objektu, volání <xref:System.Threading.Overlapped.Pack%2A> metodu k získání <xref:System.Threading.NativeOverlapped> struktura, která může být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="9cacc-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="9cacc-132">Pokud <xref:System.AppDomain> uvolní, CLR čeká na dokončení asynchronní operace před uvolněním ukazatele.</span><span class="sxs-lookup"><span data-stu-id="9cacc-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9cacc-133">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="9cacc-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="9cacc-134">Toto MDA nemělo žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="9cacc-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9cacc-135">Výstup</span><span class="sxs-lookup"><span data-stu-id="9cacc-135">Output</span></span>  
 <span data-ttu-id="9cacc-136">Následuje příklad výstupu z tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="9cacc-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="9cacc-137">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9cacc-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cacc-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cacc-138">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9cacc-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9cacc-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9cacc-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="9cacc-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
