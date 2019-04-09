---
title: vícenásobný přístup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094213"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="9fb4f-102">vícenásobný přístup MDA</span><span class="sxs-lookup"><span data-stu-id="9fb4f-102">reentrancy MDA</span></span>
<span data-ttu-id="9fb4f-103">`reentrancy` Pomocníka spravovaného ladění (MDA) se aktivuje, když je proveden pokus o přechod z nativní do spravovaného kódu v případech, kdy se neprovedla předchozí přepínač ze spravovaného do nativního kódu prostřednictvím uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9fb4f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="9fb4f-104">Symptoms</span></span>  
 <span data-ttu-id="9fb4f-105">Objekt haldy je poškozený nebo jiné závažné chyby dochází při přesunu z nativní do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="9fb4f-106">Vlákna, která přepínat mezi nativním a spravovaným kódem v obou směrech musíte provést uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="9fb4f-107">Určitých bodů rozšiřitelnosti nízké úrovně v operačním systému, jako je například vektorové obslužné rutiny výjimek, ale umožní přepínače ze spravované do nativního kódu bez uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="9fb4f-108">Tyto přepínače jsou v rámci ovládacího prvku operačního systému, nikoli ovládány language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9fb4f-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="9fb4f-109">Nativní kód, který se spustí v těmto rozšiřujícím bodům musí Vyhněte se volání zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9fb4f-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="9fb4f-110">Cause</span></span>  
 <span data-ttu-id="9fb4f-111">Bodu rozšiřitelnosti nízké úrovně operačního systému, jako je například vektorové obslužné rutiny výjimek, je aktivován při provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="9fb4f-112">Kód aplikace, která je volána pomocí tohoto bodu rozšiřitelnosti se pokouší volat zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="9fb4f-113">Tento problém je způsoben vždy kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9fb4f-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="9fb4f-114">Resolution</span></span>  
 <span data-ttu-id="9fb4f-115">Prozkoumejte trasování zásobníku pro vlákno, které se má toto MDA aktivováno.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="9fb4f-116">Vlákno se pokouší o neoprávněně volat do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="9fb4f-117">Trasování zásobníku by měl odhalit kódu aplikace pomocí tohoto bodu rozšiřitelnost, kód operačního systému, který poskytuje tento bod rozšiřitelnost a spravovaný kód, který bylo přerušeno bodu rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="9fb4f-118">Uvidíte MDA aktivováno při pokusu o volání spravovaného kódu z uvnitř vektorové obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="9fb4f-119">V zásobníku uvidíte zpracování kódu a spravovaného kódu aktivuje výjimku, jako výjimek operačního systému <xref:System.DivideByZeroException> nebo <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="9fb4f-120">V tomto příkladu je na správné řešení úplně implementace vektorové obslužné rutiny výjimek v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9fb4f-121">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="9fb4f-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="9fb4f-122">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9fb4f-123">Výstup</span><span class="sxs-lookup"><span data-stu-id="9fb4f-123">Output</span></span>  
 <span data-ttu-id="9fb4f-124">MDA hlásí, že probíhá pokus o neplatné opětovné zadání.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="9fb4f-125">Prozkoumejte zásobníku vlákna, chcete-li zjistit, proč dochází k tomu a pokyny k vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="9fb4f-126">Tady je ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="9fb4f-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9fb4f-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9fb4f-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fb4f-128">Example</span></span>  
 <span data-ttu-id="9fb4f-129">Následující příklad způsobí, že kód <xref:System.AccessViolationException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="9fb4f-130">Ve verzích Windows, která podporuje zpracování výjimek vektorové to způsobí, že spravované vektorové obslužné rutiny výjimek má být volána.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="9fb4f-131">Pokud `reentrancy` MDA je povoleno, MDA se aktivují během pokusu o volání `MyHandler` z operačního systému vektorové výjimky podporu kód pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="9fb4f-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fb4f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fb4f-132">See also</span></span>

- [<span data-ttu-id="9fb4f-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9fb4f-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
