---
title: "exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d68e3f8659b0d5fe212c58443fe9a8b42f9cef89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
