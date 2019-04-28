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
ms.openlocfilehash: 7bb4779e300df71a5d075a322bcac8398ce42f34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754437"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="8d75c-102">gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="8d75c-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="8d75c-103">`gcManagedToUnmanaged` Pomocníka spravovaného ladění (MDA) způsobí, že uvolňování paměti pokaždé, když vlákno přejde ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8d75c-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8d75c-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="8d75c-104">Symptoms</span></span>  
 <span data-ttu-id="8d75c-105">Jako součást nespravovaný uživatelský vyvolá narušení přístupu při pokusu o použití spravovaný objekt, který měl byly vystaveny objektům modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8d75c-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="8d75c-106">Zdá se, že objekt modelu COM byly vydány.</span><span class="sxs-lookup"><span data-stu-id="8d75c-106">The COM object appears to have been released.</span></span> <span data-ttu-id="8d75c-107">Porušení přístupu je nedeterministická.</span><span class="sxs-lookup"><span data-stu-id="8d75c-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8d75c-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="8d75c-108">Cause</span></span>  
 <span data-ttu-id="8d75c-109">Pokud nespravované součásti není správně spravovaný objekt modelu COM pro počítání odkazů, modul runtime může shromažďovat vystavit rozhraní COM při nespravované součásti dál obsahuje odkaz na objekt spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="8d75c-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="8d75c-110">Modul runtime zavolá <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolnění paměti, takže pokud uživatel součást používá objekt, než dojde k uvolnění paměti, pak ji nebude ještě byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="8d75c-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="8d75c-111">Toto je zdroj nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="8d75c-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8d75c-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="8d75c-112">Resolution</span></span>  
 <span data-ttu-id="8d75c-113">Povolení tohoto Pomocníka s nastavením zkracuje dobu mezi při objekt je vhodné pro kolekci a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, pomáhá sledovat, jaká součást nespravované se nejprve pokusí o přístup k shromážděné objekty.</span><span class="sxs-lookup"><span data-stu-id="8d75c-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8d75c-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="8d75c-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="8d75c-115">Pokaždé, když vlákno přechody ze spravovaného do nespravovaného kódu způsobí, že uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8d75c-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8d75c-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="8d75c-116">Output</span></span>  
 <span data-ttu-id="8d75c-117">Toto MDA negeneruje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="8d75c-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8d75c-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8d75c-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d75c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d75c-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8d75c-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8d75c-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8d75c-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="8d75c-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="8d75c-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="8d75c-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
