---
title: notMarshalable – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění notMarshalable, který se může aktivovat v případě, že volání nejsou obsluhovaná nebo se nevyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.
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
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803791"
---
# <a name="notmarshalable-mda"></a>notMarshalable – pomocník spravovaného ladění (MDA)
`notMarshalable`Pokud modul CLR (Common Language Runtime) nalezne ukazatel rozhraní modelu COM bez platného registrovaného proxy/zástupné procedury nebo nesprávná `IMarshal` implementace rozhraní při pokusu o zařazování rozhraní napříč kontexty, aktivuje se pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Volání nejsou obsluhovaná nebo se volání vyskytují v nesprávném kontextu ukazatelů rozhraní modelu COM.  
  
## <a name="cause"></a>Příčina  
 `IMarshal`Při pokusu o zařazování rozhraní napříč kontexty není k dispozici žádný platný registrovaný proxy/zástupný kód nebo nesprávný.  
  
## <a name="resolution"></a>Řešení  
 Ujistěte se, že máte registrovanou zástupnou proceduru proxy a že `IMarshal` je implementace platná.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
