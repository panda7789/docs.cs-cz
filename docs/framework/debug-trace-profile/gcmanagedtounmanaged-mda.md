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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204273"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="1bb5a-102">gcManagedToUnmanaged – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1bb5a-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="1bb5a-103">`gcManagedToUnmanaged` Pomocníka spravovaného ladění (MDA) způsobí, že uvolňování paměti pokaždé, když vlákno přejde ze spravovaného do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1bb5a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1bb5a-104">Symptoms</span></span>  
 <span data-ttu-id="1bb5a-105">Jako součást nespravovaný uživatelský vyvolá narušení přístupu při pokusu o použití spravovaný objekt, který měl byly vystaveny objektům modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="1bb5a-106">Zdá se, že objekt modelu COM byly vydány.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-106">The COM object appears to have been released.</span></span> <span data-ttu-id="1bb5a-107">Porušení přístupu je nedeterministická.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1bb5a-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="1bb5a-108">Cause</span></span>  
 <span data-ttu-id="1bb5a-109">Pokud nespravované součásti není správně spravovaný objekt modelu COM pro počítání odkazů, modul runtime může shromažďovat vystavit rozhraní COM při nespravované součásti dál obsahuje odkaz na objekt spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="1bb5a-110">Modul runtime zavolá <xref:System.Runtime.InteropServices.Marshal.Release%2A> během uvolnění paměti, takže pokud uživatel součást používá objekt, než dojde k uvolnění paměti, pak ji nebude ještě byly shromážděny.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="1bb5a-111">Toto je zdroj nondeterminism.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1bb5a-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="1bb5a-112">Resolution</span></span>  
 <span data-ttu-id="1bb5a-113">Povolení tohoto Pomocníka s nastavením zkracuje dobu mezi při objekt je vhodné pro kolekci a <xref:System.Runtime.InteropServices.Marshal.Release%2A> je volána, pomáhá sledovat, jaká součást nespravované se nejprve pokusí o přístup k shromážděné objekty.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1bb5a-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="1bb5a-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="1bb5a-115">Pokaždé, když vlákno přechody ze spravovaného do nespravovaného kódu způsobí, že uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1bb5a-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="1bb5a-116">Output</span></span>  
 <span data-ttu-id="1bb5a-117">Toto MDA negeneruje žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="1bb5a-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1bb5a-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1bb5a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bb5a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bb5a-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1bb5a-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1bb5a-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1bb5a-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="1bb5a-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="1bb5a-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="1bb5a-122">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
