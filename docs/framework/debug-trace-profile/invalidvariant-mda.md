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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 426b9df449b12d2f34fa70fc721cc050fa3e4ddd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386714"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="09254-102">invalidVariant – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="09254-102">invalidVariant MDA</span></span>
<span data-ttu-id="09254-103">`invalidVariant` Pomocník spravovaného ladění (MDA) se aktivuje, když neplatný `VARIANT` struktura je došlo během volání z nativní nebo nespravovaného kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="09254-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="09254-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="09254-104">Symptoms</span></span>  
 <span data-ttu-id="09254-105">Neočekávané chování během přechodu mezi nativní a spravované kódové zahrnující zařazování z `VARIANT` k objektu.</span><span class="sxs-lookup"><span data-stu-id="09254-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="09254-106">příčina</span><span class="sxs-lookup"><span data-stu-id="09254-106">Cause</span></span>  
 <span data-ttu-id="09254-107">Nativní kód je předávání chybná `VARIANT` struktura do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="09254-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="09254-108">Modul runtime pokusí zařazování to `VARIANT` na objekt a aktivuje MDA, pokud `VARIANT` není platný.</span><span class="sxs-lookup"><span data-stu-id="09254-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="09254-109">Příkladem neplatné `VARIANT`S zahrnout `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="09254-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="09254-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="09254-110">Resolution</span></span>  
 <span data-ttu-id="09254-111">Kód nativní nebo nespravované předávání `VARIANT` musíte zajistit, aby `VARIANT` správně vytvořen a inicializován.</span><span class="sxs-lookup"><span data-stu-id="09254-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="09254-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="09254-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="09254-113">MDA nemá žádný vliv na modul runtime chování.</span><span class="sxs-lookup"><span data-stu-id="09254-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="09254-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="09254-114">Output</span></span>  
 <span data-ttu-id="09254-115">MDA zpráva označující, že modul runtime zjistil neplatný `VARIANT` předal modul nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="09254-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="09254-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="09254-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09254-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="09254-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="09254-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="09254-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="09254-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="09254-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
