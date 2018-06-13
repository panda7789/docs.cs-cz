---
title: callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aa9ecd357a192eba64cc14f8940b264461b5e74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356352"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="80691-102">callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="80691-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="80691-103">`callbackOnCollectedDelegate` Pomocník spravovaného ladění (MDA) se aktivuje, pokud je delegáta zařazen ze spravovaného na nespravovaný kód jako ukazatel na funkci a zpětné volání je umístěn na tento ukazatel na funkci po uvolnění z paměti delegát.</span><span class="sxs-lookup"><span data-stu-id="80691-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="80691-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="80691-104">Symptoms</span></span>  
 <span data-ttu-id="80691-105">Při pokusu o volání do spravovaného kódu pomocí ukazatele na funkce, které byly získány ze spravovaných delegáti dojít k porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="80691-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="80691-106">Tyto chyby při není common language runtime (CLR) chyb, může se zdát, vzhledem k tomu, že dojde k porušení přístupu v kódu CLR.</span><span class="sxs-lookup"><span data-stu-id="80691-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="80691-107">Selhání není konzistentní; Někdy je úspěšné volání na ukazatel funkce a v některých případech se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="80691-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="80691-108">Selhání může dojít pouze v případě velkého zatížení nebo na náhodných počet pokusů.</span><span class="sxs-lookup"><span data-stu-id="80691-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="80691-109">příčina</span><span class="sxs-lookup"><span data-stu-id="80691-109">Cause</span></span>  
 <span data-ttu-id="80691-110">Delegát, ze kterého byl vytvořen a vystavené na nespravovaný kód ukazatel na funkci se uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="80691-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="80691-111">Když komponentu nespravované se pokusí zavolat na ukazatel na funkci, vygeneruje porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="80691-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="80691-112">Selhání se zobrazí náhodné, protože závisí na při uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="80691-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="80691-113">Pokud delegát je vhodné pro kolekce, kolekce paměti může vzniknout po zpětného volání a volání bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="80691-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="80691-114">V jinou dobu dojde k uvolnění paměti před zpětné volání, zpětné volání vygeneruje porušení přístupu a program se zastaví.</span><span class="sxs-lookup"><span data-stu-id="80691-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="80691-115">Pravděpodobnost selhání závisí na čas mezi zařazování delegáta a zpětného volání na ukazatel na funkci, jakož i četnost kolekce.</span><span class="sxs-lookup"><span data-stu-id="80691-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="80691-116">Selhání je výskyt občasný, pokud je krátká doba mezi zařazování delegáta a následná zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="80691-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="80691-117">Je tomu tak obvykle Pokud nespravované metoda přijetí ukazatel na funkci neukládá ukazatel funkce pro pozdější použití, ale místo toho volání zpět na ukazatel funkce okamžitě na dokončení jeho operace před vrácením.</span><span class="sxs-lookup"><span data-stu-id="80691-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="80691-118">Podobně další probíhalo uvolňování paměti při systému je přetížen, takže je pravděpodobnější, že dojde k uvolnění paměti před zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="80691-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="80691-119">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="80691-119">Resolution</span></span>  
 <span data-ttu-id="80691-120">Jakmile delegáta byl zařazen se jako ukazatel Nespravované funkce, nemůže sledovat garbage collector v celé jeho životnosti.</span><span class="sxs-lookup"><span data-stu-id="80691-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="80691-121">Místo toho kódu musí je udržovat v odkazu na delegáta po dobu jeho existence ukazatel Nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="80691-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="80691-122">Ale předtím, než můžete to udělat, je nejprve nutné určit delegáta, který byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="80691-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="80691-123">Po aktivaci MDA poskytuje název typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="80691-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="80691-124">Použijte tento název pro vyhledávání kódu pro platformu vyvolání nebo COM podpisy, které předat přidělíte nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="80691-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="80691-125">Problematické delegáta je předána jednu z těchto volání lokalit.</span><span class="sxs-lookup"><span data-stu-id="80691-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="80691-126">Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolňování před každou zpětného volání do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="80691-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="80691-127">Tato akce odebere nejistoty zaváděné uvolňování zajištěním, které kolekce paměti vždy předchází zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="80691-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="80691-128">Jakmile již víte, jaké delegáta byl shromážděn a měnit kód zachovat odkaz na tohoto delegáta na straně pro spravované po dobu jeho existence zařazené nespravované funkce ukazatele.</span><span class="sxs-lookup"><span data-stu-id="80691-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="80691-129">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="80691-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="80691-130">Když Delegáti jsou zařazené jako ukazatelů na funkce, modul runtime přiděluje převodu, která provádí přechod z nespravovaných do spravovaných.</span><span class="sxs-lookup"><span data-stu-id="80691-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="80691-131">Tato převodu je co nespravovaného kódu ve skutečnosti volá před spravovaný nakonec vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="80691-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="80691-132">Bez `callbackOnCollectedDelegate` MDA povolené, nespravovaného kódu zařazování se odstraní, jakmile se shromažďují delegát.</span><span class="sxs-lookup"><span data-stu-id="80691-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="80691-133">Pomocí `callbackOnCollectedDelegate` MDA povolené, nespravovaného kódu zařazování se neodstraní okamžitě po shromážděných delegát.</span><span class="sxs-lookup"><span data-stu-id="80691-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="80691-134">Posledních 1000 instance místo toho se ukládají zachování připojení ve výchozím nastavení a změnit tak, aby aktivovat MDA při volání.</span><span class="sxs-lookup"><span data-stu-id="80691-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="80691-135">Odstraní jinou bitovou šířku se nakonec po 1,001 více zařazené delegáti se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="80691-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="80691-136">Výstup</span><span class="sxs-lookup"><span data-stu-id="80691-136">Output</span></span>  
 <span data-ttu-id="80691-137">MDA hlásí název typu delegáta, který byl shromážděn před zpětné volání došlo k pokusu o jeho ukazatel Nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="80691-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="80691-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="80691-138">Configuration</span></span>  
 <span data-ttu-id="80691-139">Následující příklad ukazuje možnosti konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="80691-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="80691-140">Nastaví počet převody, které MDA zachová aktivní na 1 500.</span><span class="sxs-lookup"><span data-stu-id="80691-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="80691-141">Výchozí hodnota `listSize` hodnota je 1 000, minimální hodnota je 50 a maximální hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="80691-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="80691-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="80691-142">Example</span></span>  
 <span data-ttu-id="80691-143">Následující příklad znázorňuje situaci, které můžou aktivovat tuto (mda):</span><span class="sxs-lookup"><span data-stu-id="80691-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}  
// ---------------------------------------------------  
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="80691-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="80691-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="80691-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="80691-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="80691-146">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="80691-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="80691-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="80691-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
