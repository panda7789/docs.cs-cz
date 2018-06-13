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
ms.openlocfilehash: 1f1542cf9d0568fe2ec35c046c358b7249231d42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392902"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
`invalidGCHandleCookie` Pomocník spravovaného ladění (MDA) se aktivuje při převodu z neplatný <xref:System.IntPtr> k danému souboru cookie <xref:System.Runtime.InteropServices.GCHandle> dojde k pokusu o.  
  
## <a name="symptoms"></a>Příznaky  
 Není definována chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načíst <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.  
  
## <a name="cause"></a>příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyla původně vytvořena z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle> který již byl uvolněn, soubor cookie k <xref:System.Runtime.InteropServices.GCHandle> v doméně jinou aplikaci, nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předaný zpět do modulu CLR jako <xref:System.IntPtr>, kde došlo k pokusu přetypování.  
  
## <a name="resolution"></a>Rozlišení  
 Zadejte platný <xref:System.IntPtr> soubor cookie pro <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Pokud je povolena tato MDA, se již nemůže ke sledování kořeny zpět na jejich objekty, protože hodnoty souboru cookie, který je předán zpět se liší od těm, které jsou vráceny v případě, že není povolená MDA ladicího programu.  
  
## <a name="output"></a>Výstup  
 Neplatný <xref:System.IntPtr> vykazuje se hodnota souboru cookie.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
