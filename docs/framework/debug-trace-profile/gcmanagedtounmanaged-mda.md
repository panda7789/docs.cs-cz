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
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052775"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="ccf41-102">gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="ccf41-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="ccf41-103">Pomocník `gcManagedToUnmanaged` spravovaného ladění (MDA) způsobuje uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ccf41-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ccf41-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ccf41-104">Symptoms</span></span>  
 <span data-ttu-id="ccf41-105">Nespravovaná uživatelská komponenta vyvolá narušení přístupu při pokusu o použití spravovaného objektu, který byl vystaven modelu COM.</span><span class="sxs-lookup"><span data-stu-id="ccf41-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="ccf41-106">Zdá se, že objekt COM byl vydán.</span><span class="sxs-lookup"><span data-stu-id="ccf41-106">The COM object appears to have been released.</span></span> <span data-ttu-id="ccf41-107">Porušení přístupu není deterministické.</span><span class="sxs-lookup"><span data-stu-id="ccf41-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ccf41-108">příčina</span><span class="sxs-lookup"><span data-stu-id="ccf41-108">Cause</span></span>  
 <span data-ttu-id="ccf41-109">Pokud nespravovaná komponenta neodkazuje správně na počítání spravovaného objektu COM, pak modul runtime může shromáždit spravované objekty, které jsou vystaveny modelu COM v případě, že nespravované součásti stále drží odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="ccf41-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="ccf41-110">Běhové volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolňování paměti, takže pokud uživatelská komponenta používá objekt před uvolněním paměti, pak se ještě neshromáždí.</span><span class="sxs-lookup"><span data-stu-id="ccf41-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="ccf41-111">Toto je zdroj nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="ccf41-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ccf41-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="ccf41-112">Resolution</span></span>  
 <span data-ttu-id="ccf41-113">Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy je objekt způsobilý pro shromažďování <xref:System.Runtime.InteropServices.Marshal.Release%2A> a je volán, což pomáhá sledovat, která nespravované komponenty se nejprve pokusí o přístup k shromážděnému objektu.</span><span class="sxs-lookup"><span data-stu-id="ccf41-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ccf41-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="ccf41-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="ccf41-115">Způsobí uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ccf41-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ccf41-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="ccf41-116">Output</span></span>  
 <span data-ttu-id="ccf41-117">Tento MDA nevytváří žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="ccf41-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ccf41-118">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="ccf41-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccf41-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccf41-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ccf41-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="ccf41-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ccf41-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="ccf41-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="ccf41-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="ccf41-122">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
