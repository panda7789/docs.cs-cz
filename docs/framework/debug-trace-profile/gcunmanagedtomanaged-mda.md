---
title: gcUnmanagedToManaged – pomocník spravovaného ladění
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f662114868832f909d734a482e1dc9aefb841a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754476"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="68677-102">gcUnmanagedToManaged – pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="68677-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="68677-103">`gcUnmanagedToManaged` Pomocníka spravovaného ladění (MDA) způsobí, že uvolňování paměti pokaždé, když vlákno přejde z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="68677-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="68677-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="68677-104">Symptoms</span></span>  
 <span data-ttu-id="68677-105">Vyvolat pomocí modelu COM a platformy spuštěné nespravovaný uživatelský komponenty aplikace způsobuje narušení přístupu nedeterministická v CLR.</span><span class="sxs-lookup"><span data-stu-id="68677-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="68677-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="68677-106">Cause</span></span>  
 <span data-ttu-id="68677-107">Pokud aplikace běží nespravované součásti, pak tyto součásti pravděpodobně došlo k poškození haldy uvolňování.</span><span class="sxs-lookup"><span data-stu-id="68677-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="68677-108">To způsobí, že porušení přístupu v CLR systému uvolňování paměti se pokusí vás grafu objektů.</span><span class="sxs-lookup"><span data-stu-id="68677-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="68677-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="68677-109">Resolution</span></span>  
 <span data-ttu-id="68677-110">Povolení tohoto Pomocníka s nastavením zkracuje dobu mezi při nespravované součásti poškození haldy uvolňování a po porušení přístupu se stane, můžete vynutit uvolnění paměti dojde k před každý spravovaný přechod.</span><span class="sxs-lookup"><span data-stu-id="68677-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="68677-111">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="68677-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="68677-112">Pokaždé, když přechody vláken z nespravovaného do spravovaného kódu způsobí, že uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="68677-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="68677-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="68677-113">Output</span></span>  
 <span data-ttu-id="68677-114">Toto MDA negeneruje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="68677-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="68677-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="68677-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68677-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68677-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="68677-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="68677-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="68677-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="68677-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="68677-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="68677-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
