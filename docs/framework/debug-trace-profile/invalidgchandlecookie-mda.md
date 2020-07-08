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
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
V `invalidGCHandleCookie` případě, že <xref:System.IntPtr> došlo k pokusu o převod z neplatného souboru cookie na a, je aktivován pomocník spravovaného ladění (MDA) <xref:System.Runtime.InteropServices.GCHandle> .  
  
## <a name="symptoms"></a>Příznaky  
 Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr> .  
  
## <a name="cause"></a>Příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle> , představuje, <xref:System.Runtime.InteropServices.GCHandle> který již byl uvolněn, je soubor cookie do <xref:System.Runtime.InteropServices.GCHandle> jiné aplikační domény nebo byl zařazen do nativního kódu jako objekt, který byl převedený <xref:System.Runtime.InteropServices.GCHandle> zpět do CLR jako <xref:System.IntPtr> , kde došlo k pokusu o přetypování.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platný <xref:System.IntPtr> soubor cookie pro <xref:System.Runtime.InteropServices.GCHandle> .  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.  
  
## <a name="output"></a>Výstup  
 <xref:System.IntPtr>Je hlášena neplatná hodnota souboru cookie.  
  
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
