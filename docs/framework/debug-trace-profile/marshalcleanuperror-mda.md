---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění Marshalcleanuperror – (MDA), který je vyvolán, protože při čištění dočasných struktur došlo k neočekávané chybě.
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
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051607"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="41d26-103">marshalCleanupError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="41d26-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="41d26-104">`marshalCleanupError`Pokud modul CLR (Common Language Runtime) zaznamená chybu při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, je aktivována pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="41d26-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="41d26-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="41d26-105">Symptoms</span></span>  
 <span data-ttu-id="41d26-106">Při provádění přechodů nativního a spravovaného kódu dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna, není obnoven nebo dojde k chybám při <xref:System.Runtime.InteropServices.SafeHandle> čištění.</span><span class="sxs-lookup"><span data-stu-id="41d26-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="41d26-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="41d26-107">Cause</span></span>  
 <span data-ttu-id="41d26-108">Při čištění dočasných struktur došlo k neočekávané chybě.</span><span class="sxs-lookup"><span data-stu-id="41d26-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="41d26-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="41d26-109">Resolution</span></span>  
 <span data-ttu-id="41d26-110">Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> implementace destruktoru, finalizační metody a vlastního zařazovacího modulu pro chyby.</span><span class="sxs-lookup"><span data-stu-id="41d26-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="41d26-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="41d26-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="41d26-112">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="41d26-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="41d26-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="41d26-113">Output</span></span>  
 <span data-ttu-id="41d26-114">Zpráva oznamující operaci, která během čištění neproběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="41d26-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="41d26-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="41d26-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41d26-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="41d26-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="41d26-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="41d26-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="41d26-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="41d26-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
