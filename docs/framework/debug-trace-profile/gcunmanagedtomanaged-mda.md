---
title: gcUnmanagedToManaged – pomocník spravovaného ladění
description: Přečtěte si pomocníka spravovaného ladění Gcmanagedtounmanaged – v .NET. Tento MDA se může aktivovat kvůli poškození uvolňování paměti během přechodu ke spravovanému kódu.
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
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415898"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="986ba-104">gcUnmanagedToManaged – pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="986ba-104">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="986ba-105">`gcUnmanagedToManaged`Pomocník spravovaného ladění (MDA) způsobuje uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="986ba-105">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="986ba-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="986ba-106">Symptoms</span></span>  
 <span data-ttu-id="986ba-107">Aplikace, která spouští nespravované uživatelské komponenty pomocí modelu COM a vyvolání platformy, způsobuje nedeterministické porušení přístupu v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="986ba-107">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="986ba-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="986ba-108">Cause</span></span>  
 <span data-ttu-id="986ba-109">Pokud aplikace spouští nespravované uživatelské komponenty, mohou tyto součásti poškodit haldu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="986ba-109">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="986ba-110">Tím dojde k porušení přístupu v modulu CLR, když se systém uvolňování paměti pokusí projít graf objektu.</span><span class="sxs-lookup"><span data-stu-id="986ba-110">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="986ba-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="986ba-111">Resolution</span></span>  
 <span data-ttu-id="986ba-112">Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy nespravovaná komponenta poškozuje uvolňování paměti, a když dojde k narušení přístupu vynuceným uvolňováním paměti před každým spravovaným přechodem.</span><span class="sxs-lookup"><span data-stu-id="986ba-112">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="986ba-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="986ba-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="986ba-114">Způsobí uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="986ba-114">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="986ba-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="986ba-115">Output</span></span>  
 <span data-ttu-id="986ba-116">Tento MDA nevytváří žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="986ba-116">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="986ba-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="986ba-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="986ba-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="986ba-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="986ba-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="986ba-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="986ba-120">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="986ba-120">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="986ba-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="986ba-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
