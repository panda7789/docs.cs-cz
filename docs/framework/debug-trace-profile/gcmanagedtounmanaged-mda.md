---
title: gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Gcmanagedtounmanaged –. Tento soubor MDA lze aktivovat z důvodu předčasného uvolňování paměti během přechodu na nespravovaný kód.
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
ms.openlocfilehash: 76c621a1f2bb780d38228f2a84d4c77441774770
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415911"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="74f6b-104">gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="74f6b-104">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="74f6b-105">`gcManagedToUnmanaged`Pomocník spravovaného ladění (MDA) způsobuje uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="74f6b-105">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="74f6b-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="74f6b-106">Symptoms</span></span>  
 <span data-ttu-id="74f6b-107">Nespravovaná uživatelská komponenta vyvolá narušení přístupu při pokusu o použití spravovaného objektu, který byl vystaven modelu COM.</span><span class="sxs-lookup"><span data-stu-id="74f6b-107">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="74f6b-108">Zdá se, že objekt COM byl vydán.</span><span class="sxs-lookup"><span data-stu-id="74f6b-108">The COM object appears to have been released.</span></span> <span data-ttu-id="74f6b-109">Porušení přístupu není deterministické.</span><span class="sxs-lookup"><span data-stu-id="74f6b-109">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="74f6b-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="74f6b-110">Cause</span></span>  
 <span data-ttu-id="74f6b-111">Pokud nespravovaná komponenta neodkazuje správně na počítání spravovaného objektu COM, pak modul runtime může shromáždit spravované objekty, které jsou vystaveny modelu COM v případě, že nespravované součásti stále drží odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="74f6b-111">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="74f6b-112">Běhové volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolňování paměti, takže pokud uživatelská komponenta používá objekt před uvolněním paměti, pak se ještě neshromáždí.</span><span class="sxs-lookup"><span data-stu-id="74f6b-112">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="74f6b-113">Toto je zdroj nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="74f6b-113">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="74f6b-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="74f6b-114">Resolution</span></span>  
 <span data-ttu-id="74f6b-115">Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy je objekt způsobilý pro shromažďování a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volán, což pomáhá sledovat, která nespravované komponenty se nejprve pokusí o přístup k shromážděnému objektu.</span><span class="sxs-lookup"><span data-stu-id="74f6b-115">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="74f6b-116">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="74f6b-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="74f6b-117">Způsobí uvolnění paměti při každém přechodu vlákna ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="74f6b-117">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="74f6b-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="74f6b-118">Output</span></span>  
 <span data-ttu-id="74f6b-119">Tento MDA nevytváří žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="74f6b-119">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="74f6b-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="74f6b-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74f6b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="74f6b-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="74f6b-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="74f6b-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="74f6b-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="74f6b-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="74f6b-124">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="74f6b-124">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
