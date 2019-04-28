---
title: notMarshalable – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30db07ddf935b5ce13b1fe4212f7f6a40270ae93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753696"
---
# <a name="notmarshalable-mda"></a>notMarshalable – pomocník spravovaného ladění (MDA)
`notMarshalable` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) setká ukazatele rozhraní modelu COM bez platné registrované proxy/zástupné procedury nebo nesprávné `IMarshal` při pokusu o implementace rozhraní zařazování rozhraní napříč kontexty.  
  
## <a name="symptoms"></a>Příznaky  
 Volání nejsou obsluhovány nebo v chybném kontextu pro ukazatele rozhraní modelu COM dojde k volání.  
  
## <a name="cause"></a>Příčina  
 Žádný platný registrované proxy nebo zástupné procedury nebo nesprávné `IMarshal` při pokusu o zařazení rozhraní napříč kontexty.  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, že máte proxy zástupné procedury zaregistrované a že `IMarshal` implementace je platný.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Zprávu s popisem problému.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
