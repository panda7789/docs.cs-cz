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
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217515"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
Pokud je vyvolána výjimka z kódu modulu CLR (Common Language Runtime), který je volán z modelu COM prostřednictvím metody, která nemá nespravovaný návratový typ HRESULT, je aktivována aplikace `exceptionSwallowedOnCallFromCOM` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Volání spravované komponenty z modelu COM vrátí hodnotu FALSE nebo 0. Případně, pokud má metoda návratový typ void, nesmí být žádné náznaky, že při provádění metody došlo k výjimce. V tomto případě bude výjimka tiše zachycena a provádění se vrátí volajícímu modelu COM.  
  
## <a name="cause"></a>Příčina  
 Došlo k výjimce, ale neexistuje žádný platný způsob, jak ji ohlásit.  
  
## <a name="resolution"></a>Řešení  
 Pouze informativní, nemusí nutně vyindikativní chybu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o tichém zachycení výjimek.  
  
## <a name="output"></a>Výstup  
 Informační zpráva obsahující název metody, název typu a zprávu o výjimce.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
