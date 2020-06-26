---
title: dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění dirtyCastAndCallOnInterface, který je vyvolán, když jsou volání vtable s časnou vazbou provedena na rozhraních třídy s pozdní vazbou.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 2ed5589909915a261a22c48490e469ae52659c8c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416067"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
`dirtyCastAndCallOnInterface`Pomocník spravovaného ladění (MDA) je aktivován při pokusu o volání s časnou vazbou prostřednictvím vtable na rozhraní třídy, které bylo označeno pouze s pozdní vazbou.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace vyvolá narušení přístupu nebo má neočekávané chování při umísťování volání s časnou vazbou přes COM do CLR.  
  
## <a name="cause"></a>Příčina  
 Kód provádí pokus o předčasné vázání prostřednictvím metody vtable prostřednictvím rozhraní třídy, které je pouze pro pozdní vazbu. Všimněte si, že ve výchozím nastavení jsou rozhraní třídy identifikována pouze s pozdní vazbou. Mohou být také identifikovány jako pozdní vazby s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem s <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotou ( `[ClassInterface(ClassInterfaceType.AutoDispatch)]` ).  
  
## <a name="resolution"></a>Řešení  
 Doporučené řešení je definování explicitního rozhraní pro použití modelem COM a zaznamenání klientů modelu COM prostřednictvím tohoto rozhraní místo pomocí automaticky generovaného rozhraní třídy. Alternativně lze volání z modelu COM transformovat do volání s pozdní vazbou prostřednictvím `IDispatch` .  
  
 Nakonec je možné identifikovat třídu jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> ( `[ClassInterface(ClassInterfaceType.AutoDual)]` ) a umožnit tak volání počátečních vazeb z modelu COM. použití <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> je však důrazně nedoporučeno z důvodu omezení verzí popsaných v tématu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o voláních s časnou vazbou na rozhraních s pozdní vazbou.  
  
## <a name="output"></a>Výstup  
 Název metody nebo názvu pole, ke kterému se přistupovalo s časnou vazbou  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
