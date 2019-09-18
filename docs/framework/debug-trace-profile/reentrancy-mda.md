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
ms.openlocfilehash: d14ba8724659172711da44e7bb249e9d20768dbc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052339"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="c7178-102">vícenásobný přístup MDA</span><span class="sxs-lookup"><span data-stu-id="c7178-102">reentrancy MDA</span></span>
<span data-ttu-id="c7178-103">Při pokusu o přechod z nativního kódu do spravovaného kódu se aktivuje pomocník spravovanéholadění(MDA),protožepředchozípřepínačzespravovanéhodonativníhokódunebylprovedenprostřednictvímpřechodupodlepořadí.`reentrancy`</span><span class="sxs-lookup"><span data-stu-id="c7178-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c7178-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c7178-104">Symptoms</span></span>  
 <span data-ttu-id="c7178-105">Halda objektu je poškozena nebo dojde k jiným závažným chybám při přechodu z nativního kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="c7178-106">Vlákna, která přepínají mezi nativním a spravovaným kódem v obou směrech, musí provádět přechod na objednávku.</span><span class="sxs-lookup"><span data-stu-id="c7178-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="c7178-107">Nicméně některé body rozšiřitelnosti na nízké úrovni v operačním systému, jako je vektorová obslužná rutina výjimky, umožňují přepínání ze spravovaného do nativního kódu bez nutnosti přechodu do konkrétního pořadí.</span><span class="sxs-lookup"><span data-stu-id="c7178-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="c7178-108">Tyto přepínače jsou v rámci řízení operačního systému, nikoli v rámci řízení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c7178-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="c7178-109">Jakýkoliv nativní kód, který se spouští uvnitř těchto bodů rozšiřitelnosti, se musí vyhnout volání zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c7178-110">příčina</span><span class="sxs-lookup"><span data-stu-id="c7178-110">Cause</span></span>  
 <span data-ttu-id="c7178-111">Bod rozšiřitelnosti operačního systému nižší úrovně, jako je například vektorová obslužná rutina výjimky, byl aktivován při spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="c7178-112">Kód aplikace, který je vyvolán prostřednictvím tohoto bodu rozšiřitelnosti, se pokouší o zpětné volání zpět do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="c7178-113">Tento problém je vždy způsoben kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7178-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c7178-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="c7178-114">Resolution</span></span>  
 <span data-ttu-id="c7178-115">Prověřte trasování zásobníku pro vlákno, které aktivovalo Tento MDA.</span><span class="sxs-lookup"><span data-stu-id="c7178-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="c7178-116">Vlákno se pokouší o neoprávněné volání spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="c7178-117">Trasování zásobníku by mělo odhalit kód aplikace pomocí tohoto bodu rozšiřitelnosti, kódu operačního systému, který poskytuje tento bod rozšiřitelnosti, a spravovaného kódu, který byl přerušen bodem rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="c7178-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="c7178-118">Například se zobrazí informace MDA aktivované při pokusu o volání spravovaného kódu zevnitř vektorové obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="c7178-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="c7178-119">V zásobníku se zobrazí kód pro zpracování výjimek operačního systému a určitý spravovaný kód, který aktivuje výjimku, jako je <xref:System.DivideByZeroException> například <xref:System.AccessViolationException>nebo.</span><span class="sxs-lookup"><span data-stu-id="c7178-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="c7178-120">V tomto příkladu je správné řešení implementovat vektorovou obslužnou rutinu výjimky zcela v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="c7178-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7178-121">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="c7178-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7178-122">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="c7178-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7178-123">Výstup</span><span class="sxs-lookup"><span data-stu-id="c7178-123">Output</span></span>  
 <span data-ttu-id="c7178-124">Dojde k pokusu o vyřízení sestav s neplatným Vícenásobný přístup.</span><span class="sxs-lookup"><span data-stu-id="c7178-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="c7178-125">Zkontrolujte zásobník vlákna, abyste zjistili, proč k tomu dochází, a jak problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="c7178-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="c7178-126">Následuje ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="c7178-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="c7178-127">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c7178-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c7178-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7178-128">Example</span></span>  
 <span data-ttu-id="c7178-129">Následující příklad kódu způsobí, že <xref:System.AccessViolationException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c7178-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="c7178-130">Ve verzích Windows, které podporují zpracování vektorových výjimek, to způsobí, že bude volána spravovaná vektorová obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="c7178-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="c7178-131">Pokud je povolený `MyHandler` MDA,běhempokusuovolánízkódupodporyzpracovánívektorovévýjimkyvoperačnímsystému`reentrancy` se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="c7178-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7178-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7178-132">See also</span></span>

- [<span data-ttu-id="c7178-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c7178-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
