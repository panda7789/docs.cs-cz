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
ms.openlocfilehash: 876f0fe3c40cb6754b4ba714833dd160dc4de3a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176953"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
`invalidGCHandleCookie` Pomocníka spravovaného ladění (MDA) se aktivuje při převodu z neplatný <xref:System.IntPtr> soubor cookie <xref:System.Runtime.InteropServices.GCHandle> dojde k pokusu o.  
  
## <a name="symptoms"></a>Příznaky  
 Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načíst <xref:System.Runtime.InteropServices.GCHandle> ze <xref:System.IntPtr>.  
  
## <a name="cause"></a>Příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle> , který již byl uvolněn, soubor cookie k <xref:System.Runtime.InteropServices.GCHandle> v různých aplikační domény, nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předaný zpět do modulu CLR jako <xref:System.IntPtr>, kde došlo k pokusu přetypování.  
  
## <a name="resolution"></a>Řešení  
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
