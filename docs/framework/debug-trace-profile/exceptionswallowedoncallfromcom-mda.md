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
ms.openlocfilehash: b4c1cbf075ef96073061679b6d062075490f5e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390605"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
`exceptionSwallowedOnCallFromCOM` Pomocník spravovaného ladění (MDA) se aktivuje, když z společný kód language runtime (CLR) volat z COM prostřednictvím metody, která nemá nespravované HRESULT návratový typ je vyvolána výjimka.  
  
## <a name="symptoms"></a>Příznaky  
 Volání spravované součásti z modelu COM, vrátí se hodnota FALSE nebo 0. Případně pokud metoda má typ vrácené hodnoty void, mohou existovat žádné naznačeno, že došlo k výjimce během provádění metody. V takovém případě bude bezobslužně zachycena výjimka a provádění vrátí COM volajícímu.  
  
## <a name="cause"></a>příčina  
 Došlo k výjimce, ale neexistuje žádný platný způsob zprávu vytvoříte.  
  
## <a name="resolution"></a>Rozlišení  
 Informativní pouze, nikoli nutně naznačuje výslednou chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o bezobslužně zachycení výjimky.  
  
## <a name="output"></a>Výstup  
 Informační zpráva, která obsahuje název metody, název typu a zpráva o výjimce.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
