---
title: exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Exceptionswallowedoncallfromcom – v .NET. K tomuto problému MDA dojde, pokud byla vyvolána výjimka, ale neexistuje žádný dobrý způsob, jak ji ohlásit.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415950"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom – pomocník spravovaného ladění (MDA)
`exceptionSwallowedOnCallFromCOM`Pokud je vyvolána výjimka z kódu modulu CLR (Common Language Runtime), který je volán z modelu COM prostřednictvím metody, která nemá nespravovaný návratový typ HRESULT, je aktivována pomocník spravovaného ladění (MDA).  
  
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
