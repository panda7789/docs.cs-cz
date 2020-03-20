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
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181769"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="9e5fa-102">vícenásobný přístup MDA</span><span class="sxs-lookup"><span data-stu-id="9e5fa-102">reentrancy MDA</span></span>
<span data-ttu-id="9e5fa-103">Spravovaný `reentrancy` ladicí asistent (MDA) je aktivován při pokusu o přechod z nativního na spravovaný kód v případech, kdy předchozí přechod ze spravovaného na nativního kódu nebyl proveden prostřednictvím řádného přechodu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9e5fa-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="9e5fa-104">Symptoms</span></span>  
 <span data-ttu-id="9e5fa-105">Halda objektu je poškozennebo jiné závažné chyby dochází při přechodu z nativní do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="9e5fa-106">Vlákna, která přepínají mezi nativním a spravovaným kódem v obou směrech, musí provést řádný přechod.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="9e5fa-107">Některé nízkoúrovňové body rozšiřitelnosti v operačním systému, jako je například obslužná rutina vektorové výjimky, však umožňují přepínače ze spravovaného na nativního kódu bez provedení spořádaného přechodu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="9e5fa-108">Tyto přepínače jsou pod kontrolou operačního systému, nikoli pod kontrolou CLR (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="9e5fa-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="9e5fa-109">Jakýkoli nativní kód, který se spustí uvnitř těchto bodů rozšiřitelnosti, se musí vyhnout volání zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9e5fa-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="9e5fa-110">Cause</span></span>  
 <span data-ttu-id="9e5fa-111">Při provádění spravovaného kódu byl aktivován bod rozšiřitelnosti operačního systému nižší úrovně, například obslužná rutina vektorové výjimky.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="9e5fa-112">Kód aplikace, který je vyvolán prostřednictvím tohoto bodu rozšiřitelnosti se pokouší volat zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="9e5fa-113">Tento problém je vždy způsoben kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9e5fa-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="9e5fa-114">Resolution</span></span>  
 <span data-ttu-id="9e5fa-115">Zkontrolujte trasování zásobníku pro vlákno, které aktivovalo tento MDA.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="9e5fa-116">Podproces se pokouší nelegálně volat do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="9e5fa-117">Trasování zásobníku by mělo odhalit kód aplikace pomocí tohoto bodu rozšiřitelnosti, kód operačního systému, který poskytuje tento bod rozšiřitelnosti, a spravovaný kód, který byl přerušen bodem rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="9e5fa-118">Například uvidíte MDA aktivován ve snaze volat spravovaný kód zevnitř vektorované výjimky obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="9e5fa-119">V zásobníku uvidíte kód zpracování výjimek operačního systému <xref:System.DivideByZeroException> <xref:System.AccessViolationException>a některé spravované kódy, které aktivují výjimku, jako je například nebo .</span><span class="sxs-lookup"><span data-stu-id="9e5fa-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="9e5fa-120">V tomto příkladu je správné rozlišení implementovat vektorovou obslužnou rutinu výjimky zcela v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9e5fa-121">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="9e5fa-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="9e5fa-122">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9e5fa-123">Výstup</span><span class="sxs-lookup"><span data-stu-id="9e5fa-123">Output</span></span>  
 <span data-ttu-id="9e5fa-124">MDA hlásí, že se pokouší o nelegální reentrancy.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="9e5fa-125">Zkontrolujte zásobníku vlákna k určení, proč se to děje a jak opravit problém.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="9e5fa-126">Následuje ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="9e5fa-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9e5fa-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9e5fa-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e5fa-128">Example</span></span>  
 <span data-ttu-id="9e5fa-129">Následující příklad kódu <xref:System.AccessViolationException> způsobí, že vyvolá.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="9e5fa-130">Ve verzích systému Windows, které podporují zpracování vektorových výjimek, to způsobí, že bude volána spravovaná obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="9e5fa-131">Pokud `reentrancy` je povoleno MDA, MDA aktivuje během pokusu o `MyHandler` volání z operačního systému vektorované výjimky zpracování podpůrného kódu.</span><span class="sxs-lookup"><span data-stu-id="9e5fa-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e5fa-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e5fa-132">See also</span></span>

- [<span data-ttu-id="9e5fa-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9e5fa-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
