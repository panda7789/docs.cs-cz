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
ms.openlocfilehash: c789e8cb409bd4c59c91d6b646efe428afe7c86d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217244"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="cee0e-102">PInvokeStackImbalance – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="cee0e-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="cee0e-103">Pokud CLR zjistí, že Hloubka zásobníku po volání metody Invoke se neshoduje s očekávanou hloubkou zásobníku, na základě konvence volání zadané v atributu <xref:System.Runtime.InteropServices.DllImportAttribute> a deklaraci parametrů ve spravovaném podpisu, je aktivována aplikace `PInvokeStackImbalance` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="cee0e-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="cee0e-104">`PInvokeStackImbalance` MDA se implementuje jenom pro 32 platformy x86.</span><span class="sxs-lookup"><span data-stu-id="cee0e-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="cee0e-105">Služba `PInvokeStackImbalance` MDA je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="cee0e-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="cee0e-106">V aplikaci Visual Studio 2017 a novějších verzích se `PInvokeStackImbalance` MDA zobrazí v seznamu **asistenti spravovaného ladění** v dialogovém okně **nastavení výjimky** (které se zobrazí, když vyberete **ladění** > **Windows** > **Nastavení výjimek**).</span><span class="sxs-lookup"><span data-stu-id="cee0e-106">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="cee0e-107">Zaškrtnutím nebo zrušením zaškrtnutí políčka **přerušit, pokud je vyvolána** , nepovolíte nebo zakážete MDA; Určuje, zda aplikace Visual Studio vyvolá výjimku při aktivaci MDA.</span><span class="sxs-lookup"><span data-stu-id="cee0e-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="cee0e-108">Příznaky</span><span class="sxs-lookup"><span data-stu-id="cee0e-108">Symptoms</span></span>

<span data-ttu-id="cee0e-109">V aplikaci dojde k narušení přístupu nebo poškození paměti při volání vyvolání nebo po volání platformy.</span><span class="sxs-lookup"><span data-stu-id="cee0e-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="cee0e-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="cee0e-110">Cause</span></span>

<span data-ttu-id="cee0e-111">Spravovaný podpis volání vyvolání platformy nemusí odpovídat nespravovanému podpisu volané metody.</span><span class="sxs-lookup"><span data-stu-id="cee0e-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="cee0e-112">Tato neshoda může být způsobena spravovaným podpisem, který nedeklaruje správný počet parametrů, nebo nespecifikuje odpovídající velikost pro parametry.</span><span class="sxs-lookup"><span data-stu-id="cee0e-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="cee0e-113">Služba MDA může být také aktivována, protože konvence volání, která je pravděpodobně určena atributem <xref:System.Runtime.InteropServices.DllImportAttribute>, neodpovídá nespravované konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="cee0e-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="cee0e-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="cee0e-114">Resolution</span></span>

<span data-ttu-id="cee0e-115">Zkontrolujte spravovanou platformu vyvolání signatury a konvence volání, abyste ověřili shodu s signaturou a konvencí volání nativního cíle.</span><span class="sxs-lookup"><span data-stu-id="cee0e-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="cee0e-116">Zkuste explicitně specifikovat konvenci volání na spravovaných i nespravovaných stranách.</span><span class="sxs-lookup"><span data-stu-id="cee0e-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="cee0e-117">Je také možné, i když to není pravděpodobné, že nespravované funkce z nějakého důvodu vyrovnaly zásobník z nějakého jiného důvodu, jako je například Chyba v nespravovaném kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cee0e-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="cee0e-118">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="cee0e-118">Effect on the Runtime</span></span>

<span data-ttu-id="cee0e-119">Vynutí, aby volání všech platforem převzala neoptimalizovanou cestu v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cee0e-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="cee0e-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="cee0e-120">Output</span></span>

<span data-ttu-id="cee0e-121">Zpráva MDA poskytuje název volání metody vyvolání platformy, která způsobuje nerovnováhu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cee0e-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="cee0e-122">Ukázková zpráva volání metody Invoke na metodě `SampleMethod` je:</span><span class="sxs-lookup"><span data-stu-id="cee0e-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="cee0e-123">**Volání funkce PInvoke ' SampleMethod ' vyrovnalo vyvážení zásobníku. To je pravděpodobně způsobeno tím, že spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Ověřte, že konvence volání a parametry signatury PInvoke odpovídají cílovému nespravovanému podpisu.**</span><span class="sxs-lookup"><span data-stu-id="cee0e-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="cee0e-124">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cee0e-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="cee0e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cee0e-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="cee0e-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cee0e-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cee0e-127">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="cee0e-127">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
