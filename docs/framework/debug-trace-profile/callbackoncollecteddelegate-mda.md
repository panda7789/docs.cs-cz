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
ms.openlocfilehash: 8441e1b2c623126e844d8a641d7f002aef495e9d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145881"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="ed0c1-102">callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ed0c1-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="ed0c1-103">`callbackOnCollectedDelegate` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud delegát je zařazen ze spravovaného do nespravovaného kódu jako ukazatel na funkci a zpětné volání je umístěn na tento ukazatel na funkci delegáta byla uvolněna z paměti.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ed0c1-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ed0c1-104">Symptoms</span></span>  
 <span data-ttu-id="ed0c1-105">Při pokusu o volání spravovaného kódu prostřednictvím ukazatele na funkce, které jste získali z spravovaných delegáty, dojde k narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="ed0c1-106">Tyto chyby při není common language runtime (CLR) chyb, které může zobrazit, protože dojde k porušení přístupu v kódu CLR.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="ed0c1-107">Selhání není konzistentní; v některých případech bude úspěšné volání na ukazatel funkce a někdy nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="ed0c1-108">Pouze v případě velkého zatížení nebo na náhodné číslo pokusů o přihlášení, může dojít k selhání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ed0c1-109">příčina</span><span class="sxs-lookup"><span data-stu-id="ed0c1-109">Cause</span></span>  
 <span data-ttu-id="ed0c1-110">Delegát, ze kterého byla vytvořena a vystavit na nespravovaný kód ukazatel na funkci byla uvolněna z paměti.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="ed0c1-111">Když se nespravované součásti se pokusí zavolat na ukazatel funkce, generuje narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="ed0c1-112">Selhání se zobrazí náhodné, protože závisí na, když dojde k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="ed0c1-113">Pokud delegát má nárok na kolekce, kolekce uvolnění paměti může vzniknout po zpětném volání a bude volání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="ed0c1-114">V jinou dobu před zpětné volání dojde k uvolnění paměti, zpětné volání vygeneruje narušení přístupu a program se zastaví.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="ed0c1-115">Pravděpodobnost selhání závisí na čas mezi zařazování delegáta a zpětné volání na ukazatel funkce, jakož i frekvence uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="ed0c1-116">Selhání je sporadické, pokud je krátký čas mezi zařazování delegáta a následné zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="ed0c1-117">To je obvykle tento případ, pokud nespravované metoda přijímá ukazatel na funkci nelze uložit ukazatel na funkci pro pozdější použití, ale místo toho zavolá zpět na ukazatel funkce okamžitě na dokončení jeho operace před vrácením.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="ed0c1-118">Podobně další kolekce dojít, když je systém v případě velkého zatížení, což zvyšuje pravděpodobnost, že uvolňování paměti dojde před zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ed0c1-119">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="ed0c1-119">Resolution</span></span>  
 <span data-ttu-id="ed0c1-120">Jakmile si byl zařazen delegáta jako ukazatel nespravovanou funkci, systému uvolňování paměti nelze sledovat svého životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="ed0c1-121">Místo toho kód uchovává odkaz na delegáta po dobu životnosti ukazatel nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="ed0c1-122">Ale předtím, než budete moct provést, nejprve musíte určit, které delegát byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="ed0c1-123">Když MDA aktivováno, obsahuje název typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="ed0c1-124">Použijte tento název hledání kódu pro platformu vyvolání nebo COM podpisy, které předat tento delegát navýšení kapacity na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="ed0c1-125">Problematické delegáta se předává jednu z těchto místa volání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="ed0c1-126">Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolnění před každé zpětné volání do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="ed0c1-127">Tato akce odebere nejistoty zavedené kolekce paměti zajištěním uvolnění vždy předchází zpětnému volání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="ed0c1-128">Jakmile budete vědět, jaké delegáta byl shromážděn, změňte kód pro odkaz na tohoto delegáta na straně spravované pro dobu života ukazatele zařazené nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ed0c1-129">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="ed0c1-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="ed0c1-130">Když jsou delegáti zařadit jako ukazatele funkcí, modul runtime přiděluje převodní rutina, která provádí přechod z nespravovaných do spravovaných.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="ed0c1-131">Tento převod je co nespravovaný kód volá vlastně před spravovanou nakonec je vyvolán delegát.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="ed0c1-132">Bez `callbackOnCollectedDelegate` MDA povolena, nespravované zařazování kód se odstraní při delegáta se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="ed0c1-133">S `callbackOnCollectedDelegate` MDA povolena, nespravované zařazování kódu se neodstraní okamžitě po shromážděných delegáta.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="ed0c1-134">Místo toho jsou poslední 1 000 instancí udržována nehledě ve výchozím nastavení a změnit aktivovat MDA při volání.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="ed0c1-135">Po 1,001 více zařazené Delegáti jsou shromážděná se nakonec odstraní převodní rutině.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ed0c1-136">Výstup</span><span class="sxs-lookup"><span data-stu-id="ed0c1-136">Output</span></span>  
 <span data-ttu-id="ed0c1-137">MDA sestavy název typu delegáta, který byl shromážděn předtím, než došlo k pokusu o zpětné volání v jeho ukazatel nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ed0c1-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ed0c1-138">Configuration</span></span>  
 <span data-ttu-id="ed0c1-139">Následující příklad ukazuje možnosti konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="ed0c1-140">Nastaví počet převodní rutiny, které MDA zachová aktivní na 1 500.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="ed0c1-141">Výchozí hodnota `listSize` hodnota je 1 000, minimální hodnota je 50 a maximální hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ed0c1-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed0c1-142">Example</span></span>  
 <span data-ttu-id="ed0c1-143">Následující příklad ukazuje situaci, která může aktivovat toto MDA:</span><span class="sxs-lookup"><span data-stu-id="ed0c1-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed0c1-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed0c1-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="ed0c1-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ed0c1-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="ed0c1-146">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="ed0c1-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="ed0c1-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="ed0c1-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
