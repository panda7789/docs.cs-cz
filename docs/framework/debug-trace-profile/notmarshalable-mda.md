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
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217289"
---
# <a name="notmarshalable-mda"></a>notMarshalable – pomocník spravovaného ladění (MDA)
Pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné procedury nebo nesprávná implementace rozhraní `IMarshal` při pokusu o zařazování rozhraní napříč kontexty, aktivuje se Pomocník pro `notMarshalable` spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.  
  
## <a name="cause"></a>Příčina  
 Při pokusu o zařazení rozhraní mezi kontexty není k dispozici žádné platné registrované proxy/zástupné procedury nebo nesprávná `IMarshal`.  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, že máte registrovanou zástupnou proceduru proxy a že implementace `IMarshal` je platná.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva s popisem problému.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
