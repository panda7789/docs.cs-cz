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
ms.openlocfilehash: 3908663a12f0e4edd8024c7f53f21b2e82bb8dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665393"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
`invalidGCHandleCookie` Pomocníka spravovaného ladění (MDA) se aktivuje při převodu z neplatný <xref:System.IntPtr> soubor cookie <xref:System.Runtime.InteropServices.GCHandle> dojde k pokusu o.  
  
## <a name="symptoms"></a>Příznaky  
 Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načíst <xref:System.Runtime.InteropServices.GCHandle> ze <xref:System.IntPtr>.  
  
## <a name="cause"></a>Příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle> , který již byl uvolněn, soubor cookie k <xref:System.Runtime.InteropServices.GCHandle> v různých aplikační domény, nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předaný zpět do modulu CLR jako <xref:System.IntPtr>, kde došlo k pokusu přetypování.  
  
## <a name="resolution"></a>Rozlišení  
 Zadejte platný <xref:System.IntPtr> soubor cookie pro <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Pokud je toto MDA povolena, ladicí program již není možnost vysledovat kořeny zpět na objekty, protože se liší od těch, které vrátí, když není povolená MDA hodnoty souboru cookie, který je předán zpět.  
  
## <a name="output"></a>Výstup  
 Neplatný <xref:System.IntPtr> hlášená hodnota souboru cookie.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
