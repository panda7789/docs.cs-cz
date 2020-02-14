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
ms.openlocfilehash: dd4080870ae88da8d4e2055369cd36f3981f2eac
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216459"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="fe9f1-102">gcUnmanagedToManaged – pomocník spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="fe9f1-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="fe9f1-103">`gcUnmanagedToManaged` Pomocník pro spravované ladění (MDA) způsobí uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fe9f1-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="fe9f1-104">Symptoms</span></span>  
 <span data-ttu-id="fe9f1-105">Aplikace, která spouští nespravované uživatelské komponenty pomocí modelu COM a vyvolání platformy, způsobuje nedeterministické porušení přístupu v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fe9f1-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="fe9f1-106">Cause</span></span>  
 <span data-ttu-id="fe9f1-107">Pokud aplikace spouští nespravované uživatelské komponenty, mohou tyto součásti poškodit haldu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="fe9f1-108">Tím dojde k porušení přístupu v modulu CLR, když se systém uvolňování paměti pokusí projít graf objektu.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fe9f1-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="fe9f1-109">Resolution</span></span>  
 <span data-ttu-id="fe9f1-110">Povolení tohoto pomocníka zkracuje dobu mezi tím, kdy nespravovaná komponenta poškozuje uvolňování paměti, a když dojde k narušení přístupu vynuceným uvolňováním paměti před každým spravovaným přechodem.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fe9f1-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="fe9f1-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="fe9f1-112">Způsobí uvolnění paměti při každém přechodu vlákna z nespravovaného do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fe9f1-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="fe9f1-113">Output</span></span>  
 <span data-ttu-id="fe9f1-114">Tento MDA nevytváří žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="fe9f1-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fe9f1-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="fe9f1-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe9f1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe9f1-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="fe9f1-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="fe9f1-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fe9f1-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="fe9f1-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="fe9f1-119">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="fe9f1-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
