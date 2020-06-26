---
title: callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění callbackOnCollectedDelegate (MDA) v rozhraní .NET, který je vyvolán, pokud dojde ke zpětnému volání po uvolnění paměti delegáta.
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
ms.openlocfilehash: 32f02a4e65455f11f3bfa9260caae8b4e48f494e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416028"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="6179a-103">callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="6179a-103">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="6179a-104">`callbackOnCollectedDelegate`Pokud je delegát zařazen ze spravovaného do nespravovaného kódu jako ukazatel na funkci a na tento ukazatel funkce je umístěno zpětné volání, poté, co byl delegát uvolněn z paměti, je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="6179a-104">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6179a-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="6179a-105">Symptoms</span></span>  
 <span data-ttu-id="6179a-106">K narušení přístupu dojde při pokusu o volání spravovaného kódu prostřednictvím ukazatelů na funkce, které byly získány ze spravovaných delegátů.</span><span class="sxs-lookup"><span data-stu-id="6179a-106">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="6179a-107">Tyto chyby, zatímco nejsou chyby modulu CLR (Common Language Runtime), mohou vypadat tak, že v kódu CLR dojde k narušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="6179a-107">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="6179a-108">Selhání není konzistentní; v některých případech se volání na ukazatel na funkci zdaří a někdy selže.</span><span class="sxs-lookup"><span data-stu-id="6179a-108">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="6179a-109">K selhání může dojít pouze při velkém zatížení nebo při náhodném počtu pokusů.</span><span class="sxs-lookup"><span data-stu-id="6179a-109">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6179a-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="6179a-110">Cause</span></span>  
 <span data-ttu-id="6179a-111">Delegát, ze kterého byl ukazatel na funkci vytvořen a zpřístupněn nespravovanému kódu, byl shromážděn z paměti.</span><span class="sxs-lookup"><span data-stu-id="6179a-111">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="6179a-112">Když se nespravovanou součást pokusí zavolat na ukazatel na funkci, vygeneruje porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="6179a-112">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="6179a-113">Selhání se jeví jako náhodné, protože závisí na tom, kdy dojde k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6179a-113">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="6179a-114">Pokud má delegát nárok na kolekci, může dojít k uvolnění paměti po zpětném volání a volání je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6179a-114">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="6179a-115">V jinou dobu dojde k uvolnění paměti před zpětným voláním, zpětné volání vygeneruje porušení přístupu a program se zastaví.</span><span class="sxs-lookup"><span data-stu-id="6179a-115">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="6179a-116">Pravděpodobnost selhání závisí na době mezi zařazováním delegáta a zpětným voláním na ukazatel funkce a také frekvence uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6179a-116">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="6179a-117">Selhání je občas v případě, že čas mezi zařazováním delegáta a následným zpětným voláním je krátký.</span><span class="sxs-lookup"><span data-stu-id="6179a-117">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="6179a-118">To je obvykle případ, pokud nespravované metody, které obdrží ukazatel funkce, neuloží ukazatel na funkci pro pozdější použití, ale místo toho se před vrácením vrátí zpět na ukazatel funkce hned.</span><span class="sxs-lookup"><span data-stu-id="6179a-118">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="6179a-119">Podobně další uvolňování paměti dochází v případě vysoké zátěže systému, což je pravděpodobnější, že k uvolňování paměti dojde před zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="6179a-119">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6179a-120">Řešení</span><span class="sxs-lookup"><span data-stu-id="6179a-120">Resolution</span></span>  
 <span data-ttu-id="6179a-121">Po zařazování delegáta jako nespravovaného ukazatele na funkci nemůže systém uvolňování paměti sledovat svoji dobu života.</span><span class="sxs-lookup"><span data-stu-id="6179a-121">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="6179a-122">Místo toho musí váš kód uchovávat odkaz na delegáta po dobu života nespravovaného ukazatele na funkci.</span><span class="sxs-lookup"><span data-stu-id="6179a-122">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="6179a-123">Než to ale uděláte, musíte nejdřív určit, který delegát byl shromážděn.</span><span class="sxs-lookup"><span data-stu-id="6179a-123">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="6179a-124">Když je aktivováno MDA, poskytuje název typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="6179a-124">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="6179a-125">Použijte tento název k vyhledání kódu pro vyvolání nebo signatury modelu COM, které předají tento delegát do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6179a-125">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="6179a-126">Poškozený delegát se předává přes jednu z těchto webů volání.</span><span class="sxs-lookup"><span data-stu-id="6179a-126">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="6179a-127">Můžete také povolit `gcUnmanagedToManaged` službě MDA vynutit uvolňování paměti před každým zpětným voláním do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6179a-127">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="6179a-128">Tím dojde k odebrání nejistoty zavedené uvolňováním paměti tím, že zajistíte, aby se uvolňování paměti vždy před zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="6179a-128">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="6179a-129">Jakmile víte, který delegát byl shromážděn, změňte kód tak, aby zůstal na spravované straně odkaz na spravovanou stranu za dobu života zařazovacího ukazatele nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="6179a-129">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6179a-130">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="6179a-130">Effect on the Runtime</span></span>  
 <span data-ttu-id="6179a-131">Když jsou delegáti zařazeni jako ukazatelé na funkce, modul runtime přidělí převod, který provede přechod z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6179a-131">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="6179a-132">Tato rutina nespravovaného kódu ve skutečnosti volá před tím, než se spravované delegáty nakonec vyvolají.</span><span class="sxs-lookup"><span data-stu-id="6179a-132">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="6179a-133">Bez `callbackOnCollectedDelegate` povoleného MDA se nespravovaný kód pro zařazování odstraní při shromáždění delegáta.</span><span class="sxs-lookup"><span data-stu-id="6179a-133">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="6179a-134">`callbackOnCollectedDelegate`Když je povolený MDA, nespravovaný kód pro zařazování se hned po shromáždění delegáta neodstraní.</span><span class="sxs-lookup"><span data-stu-id="6179a-134">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="6179a-135">Místo toho se ve výchozím nastavení chovají poslední instance 1 000 a při volání metody MDA se změní na aktivovat.</span><span class="sxs-lookup"><span data-stu-id="6179a-135">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="6179a-136">V případě, že jsou shromažďována více zařazování delegátů, je nakonec 1 001 odstraněn převod.</span><span class="sxs-lookup"><span data-stu-id="6179a-136">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6179a-137">Výstup</span><span class="sxs-lookup"><span data-stu-id="6179a-137">Output</span></span>  
 <span data-ttu-id="6179a-138">MDA oznamuje název typu delegáta, který byl shromážděn před provedením zpětného volání na jeho nespravovaném ukazateli funkce.</span><span class="sxs-lookup"><span data-stu-id="6179a-138">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6179a-139">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6179a-139">Configuration</span></span>  
 <span data-ttu-id="6179a-140">Následující příklad ukazuje možnosti konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="6179a-140">The following example shows the application configuration options.</span></span> <span data-ttu-id="6179a-141">Nastaví počet převodní rutiny, který se zachová, takže zůstane aktivní až 1 500.</span><span class="sxs-lookup"><span data-stu-id="6179a-141">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="6179a-142">Výchozí `listSize` hodnota je 1 000, minimum je 50 a maximum je 2 000.</span><span class="sxs-lookup"><span data-stu-id="6179a-142">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6179a-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="6179a-143">Example</span></span>  
 <span data-ttu-id="6179a-144">Následující příklad ukazuje situaci, která může aktivovat Tento MDA:</span><span class="sxs-lookup"><span data-stu-id="6179a-144">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6179a-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="6179a-145">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6179a-146">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6179a-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6179a-147">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="6179a-147">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="6179a-148">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="6179a-148">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
