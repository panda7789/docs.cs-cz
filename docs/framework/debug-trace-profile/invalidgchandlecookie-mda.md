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
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216310"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="7b62f-102">invalidGCHandleCookie – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7b62f-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="7b62f-103">Při pokusu o převod z neplatného souboru cookie <xref:System.IntPtr> na <xref:System.Runtime.InteropServices.GCHandle> se aktivuje Pomocník s `invalidGCHandleCookie` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="7b62f-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7b62f-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7b62f-104">Symptoms</span></span>  
 <span data-ttu-id="7b62f-105">Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="7b62f-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7b62f-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="7b62f-106">Cause</span></span>  
 <span data-ttu-id="7b62f-107">Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle>, který již byl uvolněn, je soubor cookie <xref:System.Runtime.InteropServices.GCHandle> v jiné doméně aplikace nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>, ale předaný do CLR jako <xref:System.IntPtr>, kde došlo k pokusu o přetypování.</span><span class="sxs-lookup"><span data-stu-id="7b62f-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7b62f-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="7b62f-108">Resolution</span></span>  
 <span data-ttu-id="7b62f-109">Zadejte platný soubor cookie <xref:System.IntPtr> pro <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="7b62f-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b62f-110">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="7b62f-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="7b62f-111">Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.</span><span class="sxs-lookup"><span data-stu-id="7b62f-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7b62f-112">Výstup</span><span class="sxs-lookup"><span data-stu-id="7b62f-112">Output</span></span>  
 <span data-ttu-id="7b62f-113">Je nahlášena neplatná hodnota souboru cookie <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="7b62f-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7b62f-114">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b62f-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b62f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b62f-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="7b62f-116">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7b62f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
