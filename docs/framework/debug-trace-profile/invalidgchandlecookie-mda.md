---
title: invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052615"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="33b2e-102">invalidGCHandleCookie – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="33b2e-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="33b2e-103">V `invalidGCHandleCookie` případě, že došlo k pokusu o převod z neplatného <xref:System.IntPtr> souboru cookie na a <xref:System.Runtime.InteropServices.GCHandle> , je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="33b2e-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="33b2e-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="33b2e-104">Symptoms</span></span>  
 <span data-ttu-id="33b2e-105">Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr>z.</span><span class="sxs-lookup"><span data-stu-id="33b2e-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="33b2e-106">příčina</span><span class="sxs-lookup"><span data-stu-id="33b2e-106">Cause</span></span>  
 <span data-ttu-id="33b2e-107">Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, <xref:System.Runtime.InteropServices.GCHandle> představuje, který již byl uvolněn, <xref:System.Runtime.InteropServices.GCHandle> je soubor cookie do jiné aplikační domény nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předává se zpátky do CLR jako <xref:System.IntPtr>, kde došlo k pokusu o přetypování.</span><span class="sxs-lookup"><span data-stu-id="33b2e-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="33b2e-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="33b2e-108">Resolution</span></span>  
 <span data-ttu-id="33b2e-109">Zadejte platný <xref:System.IntPtr> soubor cookie <xref:System.Runtime.InteropServices.GCHandle>pro.</span><span class="sxs-lookup"><span data-stu-id="33b2e-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="33b2e-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="33b2e-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="33b2e-111">Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.</span><span class="sxs-lookup"><span data-stu-id="33b2e-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="33b2e-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="33b2e-112">Output</span></span>  
 <span data-ttu-id="33b2e-113">Je hlášena neplatná <xref:System.IntPtr> hodnota souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="33b2e-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="33b2e-114">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="33b2e-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33b2e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33b2e-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="33b2e-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="33b2e-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
