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
ms.openlocfilehash: b5c54b8c2600dca1c7b24ac663a6ed506ca8ef24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390507"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
`dirtyCastAndCallOnInterface` Pomocník spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o třídy rozhraní, které bylo označeno jako pozdní vazbou pouze volání časné vazby prostřednictvím vtable.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace vyvolá porušení pravidel přístupu nebo má neočekávanému chování při umísťování volání časné vazby prostřednictvím COM do modulu CLR.  
  
## <a name="cause"></a>příčina  
 Kód se pokouší volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze pozdní vazbou. Všimněte si, že třídou výchozí rozhraní považujete za probíhá pozdní vazbou jenom. Můžete také možné identifikovat jako pozdní vazbu s <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut s <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Rozlišení  
 Doporučené řešení je definovat explicitní rozhraní pro použití v modelu COM a máte klienty volání COM prostřednictvím tohoto rozhraní místo přes rozhraní automaticky vygenerované třídy. Alternativně lze je transformovat volání z modelu COM do volání pozdní vazbou prostřednictvím `IDispatch`.  
  
 Nakonec je možné k identifikaci třídy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) Chcete-li povolit volání časné umístit z modelu COM; však pomocí <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> se důrazně nedoporučuje kvůli Správa verzí omezení popsaná v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o volání časné vazby na rozhraní pozdní vazbu.  
  
## <a name="output"></a>Výstup  
 Název metody nebo název pole přistupuje časné vazby.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
