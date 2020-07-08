---
title: invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění invalidGCHandleCookie – (MDA), který se aktivuje při pokusu o převod z neplatného souboru cookie IntPtr na GCHandle.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 1063b7be902d3063717b6639564d819ef3292c0e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051295"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="da17e-103">invalidGCHandleCookie – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="da17e-103">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="da17e-104">V `invalidGCHandleCookie` případě, že <xref:System.IntPtr> došlo k pokusu o převod z neplatného souboru cookie na a, je aktivován pomocník spravovaného ladění (MDA) <xref:System.Runtime.InteropServices.GCHandle> .</span><span class="sxs-lookup"><span data-stu-id="da17e-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="da17e-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="da17e-105">Symptoms</span></span>  
 <span data-ttu-id="da17e-106">Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr> .</span><span class="sxs-lookup"><span data-stu-id="da17e-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="da17e-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="da17e-107">Cause</span></span>  
 <span data-ttu-id="da17e-108">Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle> , představuje, <xref:System.Runtime.InteropServices.GCHandle> který již byl uvolněn, je soubor cookie do <xref:System.Runtime.InteropServices.GCHandle> jiné aplikační domény nebo byl zařazen do nativního kódu jako objekt, který byl převedený <xref:System.Runtime.InteropServices.GCHandle> zpět do CLR jako <xref:System.IntPtr> , kde došlo k pokusu o přetypování.</span><span class="sxs-lookup"><span data-stu-id="da17e-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="da17e-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="da17e-109">Resolution</span></span>  
 <span data-ttu-id="da17e-110">Zadejte platný <xref:System.IntPtr> soubor cookie pro <xref:System.Runtime.InteropServices.GCHandle> .</span><span class="sxs-lookup"><span data-stu-id="da17e-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="da17e-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="da17e-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="da17e-112">Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.</span><span class="sxs-lookup"><span data-stu-id="da17e-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="da17e-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="da17e-113">Output</span></span>  
 <span data-ttu-id="da17e-114"><xref:System.IntPtr>Je hlášena neplatná hodnota souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="da17e-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="da17e-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="da17e-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="da17e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="da17e-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="da17e-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="da17e-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
