---
title: dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052866"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
Pomocník `dirtyCastAndCallOnInterface` spravovaného ladění (MDA) je aktivován při pokusu o volání s časnou vazbou prostřednictvím vtable na rozhraní třídy, které bylo označeno pouze s pozdní vazbou.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace vyvolá narušení přístupu nebo má neočekávané chování při umísťování volání s časnou vazbou přes COM do CLR.  
  
## <a name="cause"></a>příčina  
 Kód provádí pokus o předčasné vázání prostřednictvím metody vtable prostřednictvím rozhraní třídy, které je pouze pro pozdní vazbu. Všimněte si, že ve výchozím nastavení jsou rozhraní třídy identifikována pouze s pozdní vazbou. Mohou být také identifikovány jako pozdní vazby s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> s hodnotou (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Řešení  
 Doporučené řešení je definování explicitního rozhraní pro použití modelem COM a zaznamenání klientů modelu COM prostřednictvím tohoto rozhraní místo pomocí automaticky generovaného rozhraní třídy. Alternativně lze volání z modelu COM transformovat do volání s pozdní vazbou prostřednictvím `IDispatch`.  
  
 Nakonec je možné identifikovat třídu <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jako (`[ClassInterface(ClassInterfaceType.AutoDual)]`) a umožnit tak volání počátečních vazeb z modelu COM. použití <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> je však důrazně nedoporučeno z důvodu omezení verzí popsaných v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>tématu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o voláních s časnou vazbou na rozhraních s pozdní vazbou.  
  
## <a name="output"></a>Výstup  
 Název metody nebo názvu pole, ke kterému se přistupovalo s časnou vazbou  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
