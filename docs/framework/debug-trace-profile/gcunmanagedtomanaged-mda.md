---
title: "gcUnmanagedToManaged – pomocník spravovaného ladění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bc02f12a49ef65614114a056f9263f9ef7f5322
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="c79fa-102">gcUnmanagedToManaged – pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c79fa-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="c79fa-103">`gcUnmanagedToManaged` Pomocník spravovaného ladění (MDA) způsobí, že kolekce paměti vždy, když vlákno přechází z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c79fa-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c79fa-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c79fa-104">Symptoms</span></span>  
 <span data-ttu-id="c79fa-105">Aplikace běžící nespravované uživatelské komponenty pomocí COM a platforma vyvolání způsobuje narušení nedeterministická přístup v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c79fa-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c79fa-106">příčina</span><span class="sxs-lookup"><span data-stu-id="c79fa-106">Cause</span></span>  
 <span data-ttu-id="c79fa-107">Pokud aplikace běží nespravované uživatelské komponenty, pak tyto součásti pravděpodobně došlo k poškození haldy uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c79fa-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="c79fa-108">To způsobí, že porušení přístupu v modulu CLR při uvolňování paměti se pokusí vás grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="c79fa-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c79fa-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="c79fa-109">Resolution</span></span>  
 <span data-ttu-id="c79fa-110">Povolení tohoto pomocníka zkracuje dobu mezi při komponentu nespravované poškození haldy uvolňování paměti a když se stane narušení přístupu vynucením uvolňování před každý spravovaný přechod.</span><span class="sxs-lookup"><span data-stu-id="c79fa-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c79fa-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="c79fa-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c79fa-112">Vždy, když přechody přístup z více vláken z nespravovaného do spravovaného kódu způsobí, že uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c79fa-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c79fa-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="c79fa-113">Output</span></span>  
 <span data-ttu-id="c79fa-114">Tato MDA neprodukuje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="c79fa-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c79fa-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c79fa-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c79fa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c79fa-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c79fa-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c79fa-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c79fa-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="c79fa-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [<span data-ttu-id="c79fa-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="c79fa-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
