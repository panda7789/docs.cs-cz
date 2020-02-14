---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216158"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="822c5-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="822c5-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="822c5-103">Pokud se modul CLR (Common Language Runtime) vyskytne při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, se aktivuje Pomocník pro `marshalCleanupError` spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="822c5-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="822c5-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="822c5-104">Symptoms</span></span>  
 <span data-ttu-id="822c5-105">Při provádění přechodů nativních a spravovaných kódů dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna, není obnoven nebo dojde k chybám při <xref:System.Runtime.InteropServices.SafeHandle> vyčištění.</span><span class="sxs-lookup"><span data-stu-id="822c5-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="822c5-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="822c5-106">Cause</span></span>  
 <span data-ttu-id="822c5-107">Při čištění dočasných struktur došlo k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="822c5-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="822c5-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="822c5-108">Resolution</span></span>  
 <span data-ttu-id="822c5-109">Zkontrolujte všechny implementace <xref:System.Runtime.InteropServices.SafeHandle> destruktoru, finalizační metody a vlastní zařazování pro chyby.</span><span class="sxs-lookup"><span data-stu-id="822c5-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="822c5-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="822c5-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="822c5-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="822c5-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="822c5-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="822c5-112">Output</span></span>  
 <span data-ttu-id="822c5-113">Zpráva oznamující operaci, která během čištění neproběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="822c5-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="822c5-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="822c5-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="822c5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="822c5-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="822c5-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="822c5-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="822c5-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="822c5-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
