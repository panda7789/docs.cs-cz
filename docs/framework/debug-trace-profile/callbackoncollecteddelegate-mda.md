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
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174222"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="de01a-102">callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="de01a-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="de01a-103">Spravovaný `callbackOnCollectedDelegate` pomocník pro ladění (MDA) je aktivován, pokud je delegát zařazen ze spravovaného na nespravovaný kód jako ukazatel funkce a zpětné volání je umístěno na tento ukazatel funkce poté, co byl delegát uvolněn.</span><span class="sxs-lookup"><span data-stu-id="de01a-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="de01a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="de01a-104">Symptoms</span></span>  
 <span data-ttu-id="de01a-105">Při pokusu o volání spravovaného kódu prostřednictvím ukazatelů funkcí, které byly získány ze spravovaných delegátů, dochází k narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="de01a-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="de01a-106">Tyto chyby, i když nejsou běžné chyby runtime jazyka (CLR), se může zdát, že tak, protože dojde k narušení přístupu v kódu CLR.</span><span class="sxs-lookup"><span data-stu-id="de01a-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="de01a-107">Selhání není konzistentní; někdy volání na ukazatel funkce úspěšné a někdy se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="de01a-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="de01a-108">K selhání může dojít pouze při velkém zatížení nebo při náhodném počtu pokusů.</span><span class="sxs-lookup"><span data-stu-id="de01a-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="de01a-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="de01a-109">Cause</span></span>  
 <span data-ttu-id="de01a-110">Delegát, ze kterého byl vytvořen ukazatel funkce a vystaven nespravovanému kódu, byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="de01a-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="de01a-111">Když se nespravovaná komponenta pokusí volat ukazatel funkce, vygeneruje narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="de01a-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="de01a-112">Selhání se zobrazí náhodné, protože závisí na při uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="de01a-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="de01a-113">Pokud delegát je způsobilý pro sběr, uvolnění paměti může dojít po zpětné volání a volání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="de01a-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="de01a-114">Jindy dojde k uvolnění paměti před zpětné volání, zpětné volání generuje narušení přístupu a program se zastaví.</span><span class="sxs-lookup"><span data-stu-id="de01a-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="de01a-115">Pravděpodobnost selhání závisí na době mezi zařazování delegáta a zpětného volání na ukazatel funkce, jakož i četnost uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="de01a-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="de01a-116">Selhání je sporadické, pokud je krátká doba mezi zařazování delegáta a následné zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="de01a-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="de01a-117">To je obvykle případ, pokud nespravovaná metoda přijímající ukazatel funkce neuloží ukazatel funkce pro pozdější použití, ale místo toho zavolá zpět na ukazatel funkce okamžitě dokončit svou operaci před návratem.</span><span class="sxs-lookup"><span data-stu-id="de01a-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="de01a-118">Podobně další uvolnění paměti dojít, když je systém pod velkým zatížením, což je pravděpodobnější, že dojde k uvolnění paměti před zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="de01a-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="de01a-119">Řešení</span><span class="sxs-lookup"><span data-stu-id="de01a-119">Resolution</span></span>  
 <span data-ttu-id="de01a-120">Jakmile delegát byl zařazen jako ukazatel nespravované funkce, systém uvolňování paměti nemůže sledovat jeho životnost.</span><span class="sxs-lookup"><span data-stu-id="de01a-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="de01a-121">Místo toho musí váš kód uchovávat odkaz na delegáta po dobu životnosti ukazatele nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="de01a-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="de01a-122">Ale předtím, než to můžete udělat, musíte nejprve určit, který delegát byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="de01a-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="de01a-123">Při aktivaci MDA, poskytuje název typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="de01a-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="de01a-124">Tento název slouží k vyhledávání kódu pro vyvolání platformy nebo podpisy COM, které předávají tento delegát na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="de01a-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="de01a-125">Problematický delegát je předán prostřednictvím jednoho z těchto volání weby.</span><span class="sxs-lookup"><span data-stu-id="de01a-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="de01a-126">Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolnění paměti před každé zpětné volání do runtime.</span><span class="sxs-lookup"><span data-stu-id="de01a-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="de01a-127">Tím se odstraní nejistota zavedená uvolňování paměti tím, že zajistí, že uvolnění paměti vždy dojde před zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="de01a-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="de01a-128">Jakmile budete vědět, co delegát byl shromážděn, změňte kód zachovat odkaz na tohoto delegáta na spravované straně po dobu životnosti zařazeny ukazatele nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="de01a-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="de01a-129">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="de01a-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="de01a-130">Když delegáti jsou zařazeny jako ukazatele funkce, runtime přiděluje thunk, který provádí přechod z nespravované ho spravovaného.</span><span class="sxs-lookup"><span data-stu-id="de01a-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="de01a-131">Tato funkce thunk je to, co nespravovaný kód skutečně volá před spravovaný delegát je nakonec vyvolána.</span><span class="sxs-lookup"><span data-stu-id="de01a-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="de01a-132">Bez `callbackOnCollectedDelegate` mda povoleno nespravované zařazování kód je odstraněn při shromažďování delegáta.</span><span class="sxs-lookup"><span data-stu-id="de01a-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="de01a-133">S `callbackOnCollectedDelegate` MDA povoleno, nespravované zařazování kód není okamžitě odstraněn při shromažďování delegáta.</span><span class="sxs-lookup"><span data-stu-id="de01a-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="de01a-134">Místo toho posledních 1 000 instancí jsou udržovány naživu ve výchozím nastavení a změněn a aktivovat MDA při volání.</span><span class="sxs-lookup"><span data-stu-id="de01a-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="de01a-135">Thunk je nakonec odstraněn po 1 001 více zařazované delegáty jsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="de01a-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="de01a-136">Výstup</span><span class="sxs-lookup"><span data-stu-id="de01a-136">Output</span></span>  
 <span data-ttu-id="de01a-137">MDA hlásí název typu delegáta, který byl shromážděn před pokusem o zpětné volání na ukazatel nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="de01a-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="de01a-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="de01a-138">Configuration</span></span>  
 <span data-ttu-id="de01a-139">Následující příklad ukazuje možnosti konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="de01a-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="de01a-140">Nastavuje počet thunks MDA udržuje naživu na 1500.</span><span class="sxs-lookup"><span data-stu-id="de01a-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="de01a-141">Výchozí `listSize` hodnota je 1 000, minimum je 50 a maximální hodnota je 2 000.</span><span class="sxs-lookup"><span data-stu-id="de01a-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="de01a-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="de01a-142">Example</span></span>  
 <span data-ttu-id="de01a-143">Následující příklad ukazuje situaci, která může aktivovat tento MDA:</span><span class="sxs-lookup"><span data-stu-id="de01a-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
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
```

```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="de01a-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="de01a-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="de01a-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="de01a-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="de01a-146">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="de01a-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="de01a-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="de01a-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
