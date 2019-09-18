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
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie – pomocník spravovaného ladění (MDA)
V `invalidGCHandleCookie` případě, že došlo k pokusu o převod z neplatného <xref:System.IntPtr> souboru cookie na a <xref:System.Runtime.InteropServices.GCHandle> , je aktivován pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Nedefinované chování, například porušení přístupu a poškození paměti při pokusu o použití nebo načtení <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr>z.  
  
## <a name="cause"></a>příčina  
 Soubor cookie je pravděpodobně neplatný, protože nebyl původně vytvořen z <xref:System.Runtime.InteropServices.GCHandle>, <xref:System.Runtime.InteropServices.GCHandle> představuje, který již byl uvolněn, <xref:System.Runtime.InteropServices.GCHandle> je soubor cookie do jiné aplikační domény nebo byl zařazen do nativního kódu jako <xref:System.Runtime.InteropServices.GCHandle>ale předává se zpátky do CLR jako <xref:System.IntPtr>, kde došlo k pokusu o přetypování.  
  
## <a name="resolution"></a>Řešení  
 Zadejte platný <xref:System.IntPtr> soubor cookie <xref:System.Runtime.InteropServices.GCHandle>pro.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Když je tento soubor MDA povolený, ladicí program už nebude schopný trasovat kořeny zpátky na své objekty, protože hodnoty cookie předané zpět se liší od těch vrácených, když není povolený MDA.  
  
## <a name="output"></a>Výstup  
 Je hlášena neplatná <xref:System.IntPtr> hodnota souboru cookie.  
  
## <a name="configuration"></a>Konfiguraci  
  
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
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
