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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab3690cac28ef572b19cadb632662590d1ea04c7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052484"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="56619-102">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="56619-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="56619-103">Pokud modul CLR (Common Language Runtime) zaznamená chybu při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, je aktivována pomocník spravovanéholadění(MDA).`marshalCleanupError`</span><span class="sxs-lookup"><span data-stu-id="56619-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="56619-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="56619-104">Symptoms</span></span>  
 <span data-ttu-id="56619-105">Při provádění přechodů nativního a spravovaného kódu dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna <xref:System.Runtime.InteropServices.SafeHandle> , není obnoven nebo dojde k chybám při čištění.</span><span class="sxs-lookup"><span data-stu-id="56619-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="56619-106">příčina</span><span class="sxs-lookup"><span data-stu-id="56619-106">Cause</span></span>  
 <span data-ttu-id="56619-107">Při čištění dočasných struktur došlo k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="56619-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="56619-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="56619-108">Resolution</span></span>  
 <span data-ttu-id="56619-109">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> implementace destruktoru, finalizační metody a vlastního zařazovacího modulu pro chyby.</span><span class="sxs-lookup"><span data-stu-id="56619-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="56619-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="56619-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="56619-111">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="56619-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="56619-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="56619-112">Output</span></span>  
 <span data-ttu-id="56619-113">Zpráva oznamující operaci, která během čištění neproběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="56619-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="56619-114">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="56619-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56619-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56619-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="56619-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="56619-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="56619-117">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="56619-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
