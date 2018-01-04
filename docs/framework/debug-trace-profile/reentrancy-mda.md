---
title: "vícenásobný přístup MDA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a305658068e6d59f27957879c053b18742ea642f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reentrancy-mda"></a><span data-ttu-id="ec173-102">vícenásobný přístup MDA</span><span class="sxs-lookup"><span data-stu-id="ec173-102">reentrancy MDA</span></span>
<span data-ttu-id="ec173-103">`reentrancy` Pomocník spravovaného ladění (MDA) se aktivuje, když je proveden pokus o přechod z nativní do spravovaného kódu v případech, kdy nebyla provedena předchozí přepínač ze spravovaného na nativní kódu prostřednictvím uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="ec173-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ec173-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ec173-104">Symptoms</span></span>  
 <span data-ttu-id="ec173-105">Je poškozena halda objekt nebo jiné závažné chyby dochází při přechodu z nativní do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="ec173-106">Vláken, která přepínat mezi nativního a spravovaného kódu v obou směrech musíte provést uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="ec173-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="ec173-107">Však určité body rozšiřitelnosti nízké úrovně v operačním systému, jako je například obslužná rutina výjimky vectored, povolit přepínače ze spravovaných do nativního kódu bez uspořádání přechodu.</span><span class="sxs-lookup"><span data-stu-id="ec173-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="ec173-108">Tyto přepínače jsou pod kontrolou operačního systému, a nikoli podle běžného ovládacího prvku language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ec173-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="ec173-109">Nativní kód, který provede uvnitř tyto body rozšiřitelnosti musí Vyhněte se volání zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ec173-110">příčina</span><span class="sxs-lookup"><span data-stu-id="ec173-110">Cause</span></span>  
 <span data-ttu-id="ec173-111">Bod rozšiřitelnost nízké úrovně operačního systému, jako je například obslužná rutina výjimky vectored, aktivoval při provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="ec173-112">Aplikační kód, který lze vyvolat pomocí tohoto bodu rozšíření se pokouší o zpětného volání do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="ec173-113">Tento problém je způsoben vždy kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec173-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ec173-114">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="ec173-114">Resolution</span></span>  
 <span data-ttu-id="ec173-115">Zkontrolujte trasování zásobníku pro vlákno, které tento MDA aktivoval.</span><span class="sxs-lookup"><span data-stu-id="ec173-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="ec173-116">Vlákno se pokouší o nelegálního volání do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="ec173-117">Trasování zásobníku byste měli odhalit kódu aplikace pomocí tohoto bodu rozšiřitelnost, kód operačního systému, který poskytuje tento bod rozšiřitelnost a spravovaný kód, který byl přerušen bodem rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ec173-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="ec173-118">Například uvidíte MDA za pokus o volání spravovaného kódu z uvnitř obslužné rutiny výjimek vectored aktivuje.</span><span class="sxs-lookup"><span data-stu-id="ec173-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="ec173-119">V zásobníku uvidíte zpracování kód a některé spravovaného kódu, která aktivuje výjimku, jako výjimek operačního systému <xref:System.DivideByZeroException> nebo <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="ec173-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="ec173-120">V tomto příkladu je na správné řešení implementace obslužná rutina výjimky vectored zcela v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="ec173-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ec173-121">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="ec173-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="ec173-122">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ec173-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ec173-123">Výstup</span><span class="sxs-lookup"><span data-stu-id="ec173-123">Output</span></span>  
 <span data-ttu-id="ec173-124">MDA hlásí, že probíhá pokus o neplatné opětovné zadání.</span><span class="sxs-lookup"><span data-stu-id="ec173-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="ec173-125">Zkontrolujte zásobníku podprocesu určit, proč k této situaci a jak problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="ec173-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="ec173-126">Následuje příklad výstupu.</span><span class="sxs-lookup"><span data-stu-id="ec173-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="ec173-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ec173-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ec173-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec173-128">Example</span></span>  
 <span data-ttu-id="ec173-129">Následující kód například příčiny <xref:System.AccessViolationException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="ec173-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="ec173-130">Ve verzích systému Windows, které podporují vectored výjimek způsobí obslužná rutina výjimky spravované vectored k volání.</span><span class="sxs-lookup"><span data-stu-id="ec173-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="ec173-131">Pokud `reentrancy` MDA je povoleno, MDA aktivují během pokusu o volání `MyHandler` z operačního systému vectored výjimky podporu kód pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="ec173-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="ec173-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec173-132">See Also</span></span>  
 [<span data-ttu-id="ec173-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ec173-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
