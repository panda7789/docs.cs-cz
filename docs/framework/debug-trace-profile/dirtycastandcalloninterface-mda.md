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
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754710"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface – pomocník spravovaného ladění (MDA)
`dirtyCastAndCallOnInterface` Pomocníka spravovaného ladění (MDA) se aktivuje, když dojde k pokusu o volání časnou vazbou prostřednictvím tabulku vtable na třídy rozhraní, která byla označena s pozdní vazbou pouze.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace vyvolá narušení přístupu, nebo obsahuje neočekávané chování při volání časnou vazbou prostřednictvím modelu COM do CLR.  
  
## <a name="cause"></a>Příčina  
 Kód se pokouší o volání časné vazby prostřednictvím vtable prostřednictvím třídy rozhraní, které je pouze s pozdní vazbou. Všimněte si, že výchozí třídou rozhraní považujete za se s pozdní vazbou pouze. Je také možné identifikovat jako s pozdní vazbou pomocí <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> hodnotu (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Řešení  
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
