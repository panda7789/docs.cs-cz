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
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
Při pokusu o převod z neplatného souboru cookie <xref:System.IntPtr> na <xref:System.Runtime.InteropServices.GCHandle> se aktivuje Pomocník s `invalidGCHandleCookie` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.  
  
## <a name="cause"></a>Příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, představuje <xref:System.Runtime.InteropServices.GCHandle>, který již byl uvolněn, je soubor cookie <xref:System.Runtime.InteropServices.GCHandle> v jiné doméně aplikace nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>, ale předaný do CLR jako <xref:System.IntPtr>, kde došlo k pokusu o přetypování.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platný soubor cookie <xref:System.IntPtr> pro <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.  
  
## <a name="output"></a>Výstup  
 Je nahlášena neplatná hodnota souboru cookie <xref:System.IntPtr>.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
