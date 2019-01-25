---
title: exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebcd2d2f2387f478c36e84dad82d90d4d70d68e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554670"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
`exceptionSwallowedOnCallFromCOM` Pomocníka spravovaného ladění (MDA) se aktivuje, když je vyvolána výjimka z common language runtime (CLR) kódu volat z modelu COM pomocí metody, která nemá nespravovaný návratový typ HRESULT.  
  
## <a name="symptoms"></a>Příznaky  
 Volání spravované součásti z modelu COM, vrátí hodnotu FALSE nebo 0. Případně pokud metoda nemá návratový typ void, můžou existovat žádné označení, která během provádění metody došlo k výjimce. V tomto případě výjimku tiše zachytí se a vrátí provádění volajícímu modulu COM.  
  
## <a name="cause"></a>Příčina  
 Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.  
  
## <a name="resolution"></a>Rozlišení  
 Informativní pouze, není nutně indikátorem chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o tiše zachycené výjimky.  
  
## <a name="output"></a>Výstup  
 Informační zpráva obsahující název metody, název typu a zpráva o výjimce.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
