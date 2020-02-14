---
title: invalidVariant – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216277"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="c8771-102">invalidVariant – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="c8771-102">invalidVariant MDA</span></span>
<span data-ttu-id="c8771-103">Pokud při volání z nativního nebo nespravovaného kódu do spravovaného kódu dojde k neplatnému `VARIANT` struktury, aktivuje se Pomocník s `invalidVariant`em spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="c8771-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c8771-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c8771-104">Symptoms</span></span>  
 <span data-ttu-id="c8771-105">Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.</span><span class="sxs-lookup"><span data-stu-id="c8771-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c8771-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="c8771-106">Cause</span></span>  
 <span data-ttu-id="c8771-107">Nativní kód předá poškozenou strukturu `VARIANT` spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="c8771-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="c8771-108">Modul runtime se pokusí o zařazení tohoto `VARIANT` objektu a aktivuje hodnotu MDA, pokud je `VARIANT` neplatná.</span><span class="sxs-lookup"><span data-stu-id="c8771-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="c8771-109">Příklady neplatných `VARIANT`S zahrnují `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="c8771-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c8771-110">Řešení</span><span class="sxs-lookup"><span data-stu-id="c8771-110">Resolution</span></span>  
 <span data-ttu-id="c8771-111">Nativní nebo nespravovaný kód, který předává `VARIANT`, musí zajistit, aby byl `VARIANT` správně vytvořen a inicializován.</span><span class="sxs-lookup"><span data-stu-id="c8771-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8771-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="c8771-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="c8771-113">MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c8771-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c8771-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="c8771-114">Output</span></span>  
 <span data-ttu-id="c8771-115">Zpráva MDA označující, že modul runtime zjistil neplatnou `VARIANT` předal spravovanému kódu nespravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="c8771-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c8771-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c8771-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8771-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8771-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c8771-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c8771-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c8771-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="c8771-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
