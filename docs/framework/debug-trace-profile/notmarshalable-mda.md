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
ms.openlocfilehash: ddb6b0b5c2248d215245e0f881c8e7c91b13e480
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052432"
---
# <a name="notmarshalable-mda"></a>notMarshalable – pomocník spravovaného ladění (MDA)
Pomocník spravovaného ladění (MDA) je aktivován, pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné `IMarshal` procedury nebo nesprávná implementace rozhraní při pokusu o `notMarshalable` zařazování rozhraní napříč kontexty.  
  
## <a name="symptoms"></a>Příznaky  
 Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.  
  
## <a name="cause"></a>příčina  
 Při pokusu o zařazování rozhraní napříč kontexty není k dispozici žádný platný registrovaný proxy/zástupný kód nebo nesprávný `IMarshal` .  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, že máte registrovanou zástupnou proceduru `IMarshal` proxy a že je implementace platná.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na modul runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva s popisem problému.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
