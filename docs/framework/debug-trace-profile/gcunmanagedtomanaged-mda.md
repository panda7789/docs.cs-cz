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
ms.openlocfilehash: dfaa77adef7cdc21b1ad8abaca1439361a33d4b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386623"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="730dd-102">gcUnmanagedToManaged – pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="730dd-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="730dd-103">`gcUnmanagedToManaged` Pomocník spravovaného ladění (MDA) způsobí, že kolekce paměti vždy, když vlákno přechází z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="730dd-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="730dd-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="730dd-104">Symptoms</span></span>  
 <span data-ttu-id="730dd-105">Aplikace běžící nespravované uživatelské komponenty pomocí COM a platforma vyvolání způsobuje narušení nedeterministická přístup v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="730dd-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="730dd-106">příčina</span><span class="sxs-lookup"><span data-stu-id="730dd-106">Cause</span></span>  
 <span data-ttu-id="730dd-107">Pokud aplikace běží nespravované uživatelské komponenty, pak tyto součásti pravděpodobně došlo k poškození haldy uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="730dd-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="730dd-108">To způsobí, že porušení přístupu v modulu CLR při uvolňování paměti se pokusí vás grafu objektu.</span><span class="sxs-lookup"><span data-stu-id="730dd-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="730dd-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="730dd-109">Resolution</span></span>  
 <span data-ttu-id="730dd-110">Povolení tohoto pomocníka zkracuje dobu mezi při komponentu nespravované poškození haldy uvolňování paměti a když se stane narušení přístupu vynucením uvolňování před každý spravovaný přechod.</span><span class="sxs-lookup"><span data-stu-id="730dd-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="730dd-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="730dd-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="730dd-112">Vždy, když přechody přístup z více vláken z nespravovaného do spravovaného kódu způsobí, že uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="730dd-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="730dd-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="730dd-113">Output</span></span>  
 <span data-ttu-id="730dd-114">Tato MDA neprodukuje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="730dd-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="730dd-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="730dd-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="730dd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="730dd-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="730dd-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="730dd-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="730dd-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="730dd-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [<span data-ttu-id="730dd-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="730dd-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
