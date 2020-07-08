---
title: invalidVariant – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Invalidvariant –, který se vyvolá v případě, že při volání z nativního/nespravovaného kódu došlo k neplatnému typu VARIANT.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: ab1233d9faa86ef1508fa8fe2b5af46cb37bd523
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051633"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="d0d86-103">invalidVariant – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="d0d86-103">invalidVariant MDA</span></span>
<span data-ttu-id="d0d86-104">`invalidVariant`Pokud `VARIANT` při volání z nativního nebo nespravovaného kódu do spravovaného kódu dojde k neplatné struktuře, aktivuje se pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="d0d86-104">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d0d86-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="d0d86-105">Symptoms</span></span>  
 <span data-ttu-id="d0d86-106">Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.</span><span class="sxs-lookup"><span data-stu-id="d0d86-106">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d0d86-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="d0d86-107">Cause</span></span>  
 <span data-ttu-id="d0d86-108">Nativní kód předá poškozenou `VARIANT` strukturu spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="d0d86-108">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="d0d86-109">Modul runtime se pokusí ho zařadit `VARIANT` do objektu a aktivovat objekt MDA, pokud `VARIANT` není platný.</span><span class="sxs-lookup"><span data-stu-id="d0d86-109">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="d0d86-110">Příklady neplatných `VARIANT` s zahrnují `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="d0d86-110">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d0d86-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="d0d86-111">Resolution</span></span>  
 <span data-ttu-id="d0d86-112">Nativní nebo nespravovaný kód, který projde, `VARIANT` musí zajistit, aby `VARIANT` byl správně vytvořen a inicializován.</span><span class="sxs-lookup"><span data-stu-id="d0d86-112">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d0d86-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="d0d86-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="d0d86-114">MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d0d86-114">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d0d86-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="d0d86-115">Output</span></span>  
 <span data-ttu-id="d0d86-116">Zpráva MDA označující, že modul runtime zjistil neplatnou chybu `VARIANT` předanou spravovanému modulu spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="d0d86-116">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d0d86-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d0d86-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0d86-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d86-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d0d86-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="d0d86-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d0d86-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="d0d86-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
