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
ms.openlocfilehash: 4ff7286eb104f36ceb5e1d9b30f4a265fb068d3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564666"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError – pomocník spravovaného ladění (MDA)
`marshalCleanupError` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) dojde k chybě při pokusu o Vyčištění dočasné struktury a paměť používanou pro zařazování typů dat mezi hranice nativního a spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Nevracení paměti dochází při provádění přechody nativního a spravovaného kódu, modulu runtime stavu, například jazyková verze vlákna se neobnoví, nebo dojde k chybám v <xref:System.Runtime.InteropServices.SafeHandle> vyčištění.  
  
## <a name="cause"></a>Příčina  
 Při čištění dočasné struktury došlo k neočekávané chybě.  
  
## <a name="resolution"></a>Rozlišení  
 Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> destruktor, finalizační metody a vlastní zařazovací modul implementace chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
