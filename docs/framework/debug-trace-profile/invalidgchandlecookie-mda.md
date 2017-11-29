---
title: "invalidGCHandleCookie – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4757298a382085c1ffebc9a04e41eea81c31941b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="5b216-102">invalidGCHandleCookie – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="5b216-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="5b216-103">`invalidGCHandleCookie` Pomocník spravovaného ladění (MDA) se aktivuje při převodu z neplatný <xref:System.IntPtr> k danému souboru cookie <xref:System.Runtime.InteropServices.GCHandle> dojde k pokusu o.</span><span class="sxs-lookup"><span data-stu-id="5b216-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5b216-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="5b216-104">Symptoms</span></span>  
 <span data-ttu-id="5b216-105">Není definována chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načíst <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="5b216-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5b216-106">příčina</span><span class="sxs-lookup"><span data-stu-id="5b216-106">Cause</span></span>  
 <span data-ttu-id="5b216-107">Soubor cookie je pravděpodobně neplatný, protože nebyla původně vytvořena z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle> který již byl uvolněn, soubor cookie k <xref:System.Runtime.InteropServices.GCHandle> v doméně jinou aplikaci, nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předaný zpět do modulu CLR jako <xref:System.IntPtr>, kde došlo k pokusu přetypování.</span><span class="sxs-lookup"><span data-stu-id="5b216-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5b216-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="5b216-108">Resolution</span></span>  
 <span data-ttu-id="5b216-109">Zadejte platný <xref:System.IntPtr> soubor cookie pro <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="5b216-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5b216-110">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="5b216-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5b216-111">Pokud je povolena tato MDA, se již nemůže ke sledování kořeny zpět na jejich objekty, protože hodnoty souboru cookie, který je předán zpět se liší od těm, které jsou vráceny v případě, že není povolená MDA ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="5b216-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5b216-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="5b216-112">Output</span></span>  
 <span data-ttu-id="5b216-113">Neplatný <xref:System.IntPtr> vykazuje se hodnota souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="5b216-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5b216-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b216-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b216-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b216-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [<span data-ttu-id="5b216-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="5b216-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
