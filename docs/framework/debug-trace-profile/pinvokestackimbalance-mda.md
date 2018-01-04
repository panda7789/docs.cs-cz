---
title: "pInvokeStackImbalance – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9da05a84568a6168ed9f450afa48aa6864ed575
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="10809-102">pInvokeStackImbalance – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="10809-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="10809-103">`pInvokeStackImbalance` Pomocník spravovaného ladění (MDA) se aktivuje, když modulu CLR zjistí, že hloubka zásobníku po volání nespravovaného neodpovídá očekávané zásobníku hloubka, danou konvence volání, které jsou zadané v <xref:System.Runtime.InteropServices.DllImportAttribute> atribut společně s prohlášení o parametrech v spravované podpis.</span><span class="sxs-lookup"><span data-stu-id="10809-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10809-104">`pInvokeStackImbalance` MDA je implementována pouze pro 32-bit x86 platformy.</span><span class="sxs-lookup"><span data-stu-id="10809-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10809-105">V rozhraní .NET Framework verze 3.5 `pInvokeStackImbalance` MDA ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="10809-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="10809-106">Při použití rozhraní .NET Framework verze 3.5 s Visual Studio 2005 `pInvokeStackImbalance` MDA se objeví v **Pomocníci spravovaného ladění** seznamu v **výjimky** dialogové okno (což je zobrazí, když kliknutí na tlačítko **výjimky** na **ladění** nabídky).</span><span class="sxs-lookup"><span data-stu-id="10809-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="10809-107">Ale zaškrtnete nebo zrušíte zaškrtnutí **vyvolaná** zaškrtnutí políčka pro `pInvokeStackImbalance` povolit nebo zakázat MDA; pouze řídí, zda Visual Studio vyvolá výjimku, pokud je aktivován (mda).</span><span class="sxs-lookup"><span data-stu-id="10809-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="10809-108">Příznaky</span><span class="sxs-lookup"><span data-stu-id="10809-108">Symptoms</span></span>  
 <span data-ttu-id="10809-109">Aplikace dojde narušení přístupu nebo paměti při vytváření nebo následující platformu poškození vyvolat volání.</span><span class="sxs-lookup"><span data-stu-id="10809-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="10809-110">příčina</span><span class="sxs-lookup"><span data-stu-id="10809-110">Cause</span></span>  
 <span data-ttu-id="10809-111">Spravované podpis platformy vyvolat volání nespravovaného podpis metody volané se nemusí shodovat.</span><span class="sxs-lookup"><span data-stu-id="10809-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="10809-112">Tato neshoda může být způsobeno spravované podpis není deklarace správný počet parametrů nebo není zadáte odpovídající velikost pro parametry.</span><span class="sxs-lookup"><span data-stu-id="10809-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="10809-113">MDA můžete také aktivovat, protože konvence volání, které by mohly mít určeného <xref:System.Runtime.InteropServices.DllImportAttribute> atribut, neodpovídá nespravované konvence volání.</span><span class="sxs-lookup"><span data-stu-id="10809-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="10809-114">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="10809-114">Resolution</span></span>  
 <span data-ttu-id="10809-115">Zkontrolujte spravovaná platforma vyvolání podpis a konvence volání potvrďte, že odpovídá podpisu a konvence volání nativní cíle.</span><span class="sxs-lookup"><span data-stu-id="10809-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="10809-116">Zkuste explicitně zadat konvence volání na spravovaných a nespravovaných stranách.</span><span class="sxs-lookup"><span data-stu-id="10809-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="10809-117">Je také možné, i když ne jako pravděpodobné, že nevyvážené nespravované funkce v zásobníku z jiného důvodu, jako je například chyby v nespravované kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10809-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="10809-118">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="10809-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="10809-119">Vynutí vyvolání všechny platformy volání cestou nonoptimized v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="10809-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="10809-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="10809-120">Output</span></span>  
 <span data-ttu-id="10809-121">Zpráva MDA poskytuje název platformy vyvolat volání metody, která je příčinou nevyváženosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="10809-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="10809-122">Volání metody vyvolání ukázkovou zprávu platformy `SampleMethod` je:</span><span class="sxs-lookup"><span data-stu-id="10809-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="10809-123">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="10809-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10809-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="10809-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="10809-125">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="10809-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="10809-126">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="10809-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
