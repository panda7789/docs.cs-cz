---
title: "invalidVariant – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97fb7f9bdb144f2b586c387f33211734f664eb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="004e5-102">invalidVariant – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="004e5-102">invalidVariant MDA</span></span>
<span data-ttu-id="004e5-103">`invalidVariant` Pomocník spravovaného ladění (MDA) se aktivuje, když neplatný `VARIANT` struktura je došlo během volání z nativní nebo nespravovaného kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="004e5-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="004e5-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="004e5-104">Symptoms</span></span>  
 <span data-ttu-id="004e5-105">Neočekávané chování během přechodu mezi nativní a spravované kódové zahrnující zařazování z `VARIANT` k objektu.</span><span class="sxs-lookup"><span data-stu-id="004e5-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="004e5-106">příčina</span><span class="sxs-lookup"><span data-stu-id="004e5-106">Cause</span></span>  
 <span data-ttu-id="004e5-107">Nativní kód je předávání chybná `VARIANT` struktura do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="004e5-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="004e5-108">Modul runtime pokusí zařazování to `VARIANT` na objekt a aktivuje MDA, pokud `VARIANT` není platný.</span><span class="sxs-lookup"><span data-stu-id="004e5-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="004e5-109">Příkladem neplatné `VARIANT`S zahrnout `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="004e5-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="004e5-110">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="004e5-110">Resolution</span></span>  
 <span data-ttu-id="004e5-111">Kód nativní nebo nespravované předávání `VARIANT` musíte zajistit, aby `VARIANT` správně vytvořen a inicializován.</span><span class="sxs-lookup"><span data-stu-id="004e5-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="004e5-112">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="004e5-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="004e5-113">MDA nemá žádný vliv na modul runtime chování.</span><span class="sxs-lookup"><span data-stu-id="004e5-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="004e5-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="004e5-114">Output</span></span>  
 <span data-ttu-id="004e5-115">MDA zpráva označující, že modul runtime zjistil neplatný `VARIANT` předal modul nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="004e5-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="004e5-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="004e5-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="004e5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="004e5-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="004e5-118">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="004e5-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="004e5-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="004e5-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
