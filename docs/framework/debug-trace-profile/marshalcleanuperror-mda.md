---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6784848a5103dc9206267fc25fe7457257624cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392028"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError – pomocník spravovaného ladění (MDA)
`marshalCleanupError` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť použitá pro zařazování typů dat mezi hranice nativního a spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení paměti dojde při provádění přechody nativního a spravovaného kódu, modul runtime stavu, jako je tato funkce nebude obnovena jazykovou verzi vlákna nebo dojít k chybám v <xref:System.Runtime.InteropServices.SafeHandle> čištění.  
  
## <a name="cause"></a>příčina  
 Došlo k neočekávané chybě při čištění dočasné struktury.  
  
## <a name="resolution"></a>Rozlišení  
 Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> – destruktor, finalizační metodu a implementace vlastní chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva reporting operace, které selhaly během čištění.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
