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
ms.openlocfilehash: 8a1d8aa391b546d02c813e1f719601b9bff198be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657230"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
`dirtyCastAndCallOnInterface` Pomocníka spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o volání časnou vazbou prostřednictvím tabulku vtable na třídy rozhraní, která byla označena s pozdní vazbou pouze.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace vyvolá narušení přístupu, nebo obsahuje neočekávané chování při volání časnou vazbou prostřednictvím modelu COM do CLR.  
  
## <a name="cause"></a>Příčina  
 Kód se pokouší o volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze s pozdní vazbou. Všimněte si, že výchozí třídou rozhraní považujete za se s pozdní vazbou pouze. Je také možné identifikovat jako s pozdní vazbou pomocí <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Rozlišení  
 Doporučené řešení je definovat explicitní rozhraní pro použití modelem COM a mít volání klienty modelu COM prostřednictvím tohoto rozhraní místo přes rozhraní automaticky generovanou třídu. Alternativně je možné transformovat volání z modelu COM do volání s pozdní vazbou prostřednictvím `IDispatch`.  
  
 Nakonec je možné identifikovat třídu jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) Chcete-li povolit volání časné umístit z modelu COM; však pomocí <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> se důrazně nedoporučuje kvůli omezení správy verzí je popsáno v <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o volání časné vazby na rozhraní s pozdní vazbou.  
  
## <a name="output"></a>Výstup  
 Název metody nebo název pole, ke kterému přistupujete časné vazby.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
