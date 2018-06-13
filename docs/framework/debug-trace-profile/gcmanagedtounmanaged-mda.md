---
title: gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9be8165af499729c7b3a95c480cb64d0200e23fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386610"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="15860-102">gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="15860-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="15860-103">`gcManagedToUnmanaged` Pomocník spravovaného ladění (MDA) způsobí, že kolekce paměti vždy, když vlákno přejde ze spravovaného na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="15860-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="15860-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="15860-104">Symptoms</span></span>  
 <span data-ttu-id="15860-105">Při pokusu o použití spravovaný objekt, který byl vystaven COM., vyvolá komponentu nespravované uživatele porušení přístupu</span><span class="sxs-lookup"><span data-stu-id="15860-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="15860-106">Zdá se, že objekt COM byly vydány.</span><span class="sxs-lookup"><span data-stu-id="15860-106">The COM object appears to have been released.</span></span> <span data-ttu-id="15860-107">Narušení přístupu není deterministický.</span><span class="sxs-lookup"><span data-stu-id="15860-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="15860-108">příčina</span><span class="sxs-lookup"><span data-stu-id="15860-108">Cause</span></span>  
 <span data-ttu-id="15860-109">Pokud komponentu nespravované není správně spravovaného objektu COM při počítání referencí, může shromažďovat modulu runtime spravovaného objektu vystaven objektům modelu COM, když komponentu nespravované dál obsahuje odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="15860-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="15860-110">Volání modulu runtime <xref:System.Runtime.InteropServices.Marshal.Release%2A> během kolekce, takže pokud komponentu uživatel používá objekt předtím, než dojde k uvolnění paměti, pak jej nebude ještě byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="15860-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="15860-111">Toto je zdroj nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="15860-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="15860-112">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="15860-112">Resolution</span></span>  
 <span data-ttu-id="15860-113">Povolení tohoto pomocníka zkracuje čas mezi když je objekt v vhodné pro kolekce a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, pomáhá sledovat, která nespravované komponenta nejprve pokusí o přístup k objektu shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="15860-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="15860-114">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="15860-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="15860-115">Vždy, když přechodů přístup z více vláken ze spravovaného na nespravovaný kód způsobí, že uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="15860-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="15860-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="15860-116">Output</span></span>  
 <span data-ttu-id="15860-117">Tato MDA neprodukuje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="15860-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="15860-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="15860-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15860-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="15860-119">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="15860-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="15860-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="15860-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="15860-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="15860-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="15860-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
