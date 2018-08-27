---
title: pInvokeStackImbalance – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5594166081c36fbda1e5d1a62e017aaceb7a553d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912111"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="7b9e7-102">PInvokeStackImbalance – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7b9e7-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="7b9e7-103">`PInvokeStackImbalance` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR zjistí, že hloubka zásobníku po vyvolání platformy volání neodpovídá očekávané zásobníku hloubky, zadané konvence volání zadaná v <xref:System.Runtime.InteropServices.DllImportAttribute> atribut a deklarace parametrů v spravovaný podpis.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="7b9e7-104">`PInvokeStackImbalance` MDA je implementované jenom pro x86 32bitové platformy.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="7b9e7-105">`PInvokeStackImbalance` MDA je ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="7b9e7-106">V sadě Visual Studio 2017 `PInvokeStackImbalance` MDA se zobrazí v **asistentů spravovaného ladění** v seznamu **nastavení výjimek** dialogové okno (který se zobrazí po výběru **ladění**  >  **Windows** > **nastavení výjimek**).</span><span class="sxs-lookup"><span data-stu-id="7b9e7-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="7b9e7-107">Ale zaškrtnutím nebo zrušením zaškrtnutí **přerušení při vyvolání** zaškrtněte políčko Povolit nebo zakázat MDA; pouze určuje, zda sady Visual Studio vyvolá výjimku, když MDA aktivováno.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="7b9e7-108">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7b9e7-108">Symptoms</span></span>

<span data-ttu-id="7b9e7-109">Aplikace zjistí narušením přístupu nebo paměti, volání funkce invoke poškození při vytváření nebo následující platformy.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="7b9e7-110">příčina</span><span class="sxs-lookup"><span data-stu-id="7b9e7-110">Cause</span></span>

<span data-ttu-id="7b9e7-111">Volání funkce invoke spravovaný podpis platformy se nemusí shodovat nespravovanému podpisu volané metody.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="7b9e7-112">K této neshodě může být způsobeno spravovaný podpis nedeklarováním správný počet parametrů nebo bez zadání odpovídající velikost pro parametry.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="7b9e7-113">MDA lze také aktivovat, protože konvence volání, může být určeno <xref:System.Runtime.InteropServices.DllImportAttribute> atribut, se neshoduje s konvence nespravovaného volání.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="7b9e7-114">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="7b9e7-114">Resolution</span></span>

<span data-ttu-id="7b9e7-115">Kontrola spravovanou platformu vyvolání podpis a konvence volání pro potvrzení, že odpovídá podpisu a konvence volání nativní cíle.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="7b9e7-116">Zkuste explicitně zadat konvence volání na spravovaných a nespravovaných stranách.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="7b9e7-117">Je také možné, i když ne jako pravděpodobné, že nespravovanou funkci nevyvážená zásobníku nějakého jiného důvodu, jako jsou chyby v nespravované kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b9e7-118">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="7b9e7-118">Effect on the Runtime</span></span>

<span data-ttu-id="7b9e7-119">Vynutí všechny nespravovaného volání nonoptimized cestou v CLR.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="7b9e7-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="7b9e7-120">Output</span></span>

<span data-ttu-id="7b9e7-121">Zpráva MDA poskytuje název platformy vyvolat volání metody, která je příčinou nevyváženosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b9e7-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="7b9e7-122">Ukázková zpráva platformy vyvolání volání metody `SampleMethod` je:</span><span class="sxs-lookup"><span data-stu-id="7b9e7-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="7b9e7-123">**Zásobník má nevyvážená volání funkce PInvoke "SampleMethod". To je pravděpodobné, protože spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Zkontrolujte, jestli se konvence volání a parametry podpisu PInvoke odpovídají cílovému nespravovanému podpisu.**</span><span class="sxs-lookup"><span data-stu-id="7b9e7-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="7b9e7-124">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b9e7-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="7b9e7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b9e7-125">See Also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7b9e7-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7b9e7-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7b9e7-127">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="7b9e7-127">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
