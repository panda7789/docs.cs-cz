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
ms.openlocfilehash: eb14e0df5396d92eb223dde2e562684c4c318295
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217571"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="88e75-102">callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="88e75-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="88e75-103">Pokud je delegát zařazen ze spravovaného do nespravovaného kódu jako ukazatel na funkci a na tento ukazatel funkce je po uvolnění paměti pro tento ukazatel na funkci zpětného volání, je aktivován Pomocník pro ladění `callbackOnCollectedDelegate`.</span><span class="sxs-lookup"><span data-stu-id="88e75-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="88e75-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="88e75-104">Symptoms</span></span>  
 <span data-ttu-id="88e75-105">K narušení přístupu dojde při pokusu o volání spravovaného kódu prostřednictvím ukazatelů na funkce, které byly získány ze spravovaných delegátů.</span><span class="sxs-lookup"><span data-stu-id="88e75-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="88e75-106">Tyto chyby, zatímco nejsou chyby modulu CLR (Common Language Runtime), mohou vypadat tak, že v kódu CLR dojde k narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="88e75-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="88e75-107">Selhání není konzistentní; v některých případech se volání na ukazatel na funkci zdaří a někdy selže.</span><span class="sxs-lookup"><span data-stu-id="88e75-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="88e75-108">K selhání může dojít pouze při velkém zatížení nebo při náhodném počtu pokusů.</span><span class="sxs-lookup"><span data-stu-id="88e75-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="88e75-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="88e75-109">Cause</span></span>  
 <span data-ttu-id="88e75-110">Delegát, ze kterého byl ukazatel na funkci vytvořen a zpřístupněn nespravovanému kódu, byl shromážděn z paměti.</span><span class="sxs-lookup"><span data-stu-id="88e75-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="88e75-111">Když se nespravovanou součást pokusí zavolat na ukazatel na funkci, vygeneruje porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="88e75-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="88e75-112">Selhání se jeví jako náhodné, protože závisí na tom, kdy dojde k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="88e75-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="88e75-113">Pokud má delegát nárok na kolekci, může dojít k uvolnění paměti po zpětném volání a volání je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="88e75-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="88e75-114">V jinou dobu dojde k uvolnění paměti před zpětným voláním, zpětné volání vygeneruje porušení přístupu a program se zastaví.</span><span class="sxs-lookup"><span data-stu-id="88e75-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="88e75-115">Pravděpodobnost selhání závisí na době mezi zařazováním delegáta a zpětným voláním na ukazatel funkce a také frekvence uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="88e75-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="88e75-116">Selhání je občas v případě, že čas mezi zařazováním delegáta a následným zpětným voláním je krátký.</span><span class="sxs-lookup"><span data-stu-id="88e75-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="88e75-117">To je obvykle případ, pokud nespravované metody, které obdrží ukazatel funkce, neuloží ukazatel na funkci pro pozdější použití, ale místo toho se před vrácením vrátí zpět na ukazatel funkce hned.</span><span class="sxs-lookup"><span data-stu-id="88e75-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="88e75-118">Podobně další uvolňování paměti dochází v případě vysoké zátěže systému, což je pravděpodobnější, že k uvolňování paměti dojde před zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="88e75-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="88e75-119">Řešení</span><span class="sxs-lookup"><span data-stu-id="88e75-119">Resolution</span></span>  
 <span data-ttu-id="88e75-120">Po zařazování delegáta jako nespravovaného ukazatele na funkci nemůže systém uvolňování paměti sledovat svoji dobu života.</span><span class="sxs-lookup"><span data-stu-id="88e75-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="88e75-121">Místo toho musí váš kód uchovávat odkaz na delegáta po dobu života nespravovaného ukazatele na funkci.</span><span class="sxs-lookup"><span data-stu-id="88e75-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="88e75-122">Než to ale uděláte, musíte nejdřív určit, který delegát byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="88e75-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="88e75-123">Když je aktivováno MDA, poskytuje název typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="88e75-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="88e75-124">Použijte tento název k vyhledání kódu pro vyvolání nebo signatury modelu COM, které předají tento delegát do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="88e75-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="88e75-125">Poškozený delegát se předává přes jednu z těchto webů volání.</span><span class="sxs-lookup"><span data-stu-id="88e75-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="88e75-126">Můžete také povolit `gcUnmanagedToManaged` MDA, aby vynutilo uvolňování paměti před každým zpětným voláním do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="88e75-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="88e75-127">Tím dojde k odebrání nejistoty zavedené uvolňováním paměti tím, že zajistíte, aby se uvolňování paměti vždy před zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="88e75-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="88e75-128">Jakmile víte, který delegát byl shromážděn, změňte kód tak, aby zůstal na spravované straně odkaz na spravovanou stranu za dobu života zařazovacího ukazatele nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="88e75-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="88e75-129">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="88e75-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="88e75-130">Když jsou delegáti zařazeni jako ukazatelé na funkce, modul runtime přidělí převod, který provede přechod z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="88e75-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="88e75-131">Tato rutina nespravovaného kódu ve skutečnosti volá před tím, než se spravované delegáty nakonec vyvolají.</span><span class="sxs-lookup"><span data-stu-id="88e75-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="88e75-132">Bez povoleného `callbackOnCollectedDelegate` MDA se nespravovaný kód zařazování odstraní při shromáždění delegáta.</span><span class="sxs-lookup"><span data-stu-id="88e75-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="88e75-133">Když je povolený `callbackOnCollectedDelegate` MDA, nespravovaný kód pro zařazování se hned po shromáždění delegáta neodstraní.</span><span class="sxs-lookup"><span data-stu-id="88e75-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="88e75-134">Místo toho se ve výchozím nastavení chovají poslední instance 1 000 a při volání metody MDA se změní na aktivovat.</span><span class="sxs-lookup"><span data-stu-id="88e75-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="88e75-135">V případě, že jsou shromažďována více zařazování delegátů, je nakonec 1 001 odstraněn převod.</span><span class="sxs-lookup"><span data-stu-id="88e75-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="88e75-136">Výstup</span><span class="sxs-lookup"><span data-stu-id="88e75-136">Output</span></span>  
 <span data-ttu-id="88e75-137">MDA oznamuje název typu delegáta, který byl shromážděn před provedením zpětného volání na jeho nespravovaném ukazateli funkce.</span><span class="sxs-lookup"><span data-stu-id="88e75-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="88e75-138">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="88e75-138">Configuration</span></span>  
 <span data-ttu-id="88e75-139">Následující příklad ukazuje možnosti konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="88e75-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="88e75-140">Nastaví počet převodní rutiny, který se zachová, takže zůstane aktivní až 1 500.</span><span class="sxs-lookup"><span data-stu-id="88e75-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="88e75-141">Výchozí hodnota `listSize` je 1 000, minimum je 50 a maximum je 2 000.</span><span class="sxs-lookup"><span data-stu-id="88e75-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="88e75-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e75-142">Example</span></span>  
 <span data-ttu-id="88e75-143">Následující příklad ukazuje situaci, která může aktivovat Tento MDA:</span><span class="sxs-lookup"><span data-stu-id="88e75-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88e75-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="88e75-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="88e75-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="88e75-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="88e75-146">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="88e75-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="88e75-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="88e75-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
