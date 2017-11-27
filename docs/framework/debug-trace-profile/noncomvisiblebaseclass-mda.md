---
title: "nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b43ad5c039be3ad1c4e57bad12304927a76fb6c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
`nonComVisibleBaseClass` Pomocník spravovaného ladění (MDA) se aktivuje při `QueryInterface` COM – viditelné spravované třídy, která je odvozena ze základní třídy, které nejsou viditelné modelu COM Přišla žádost kódem nativní nebo nespravované na obálka volatelná aplikacemi COM (doleva).  `QueryInterface` Volání způsobí, že MDA aktivovat pouze v případech, kdy volání požaduje třídy rozhraní nebo výchozí `IDispatch` COM-viditelných spravované třídy.  MDA není aktivované, když `QueryInterface` je pro explicitní rozhraní, které má <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použít atribut a je explicitně implementované COM – viditelné třídy.  
  
## <a name="symptoms"></a>Příznaky  
 A `QueryInterface` volání z nativní kód, který se nedaří s hodnotou HRESULT COR_E_INVALIDOPERATION.  Hodnota HRESULT může být způsobeno runtime zakazuje `QueryInterface` volání, které by způsobily aktivace této (mda).  
  
## <a name="cause"></a>příčina  
 Modul runtime nemůže povolit `QueryInterface` volání pro třídu rozhraní nebo výchozí `IDispatch` rozhraní COM – viditelné třídy, která je odvozena od třídy, která není viditelná COM z důvodu potenciální problémy se správou verzí.  Například pokud všechny veřejné členy byly přidány do základní třídu, která není viditelná COM, existující klientů modelu COM pomocí odvozená třída může potenciálně rozdělit protože by tím například změnit vtable odvozené třídy, která obsahuje členy základní třídy, změníte.  Explicitní rozhraní vystaven objektům modelu COM nemají tento problém, protože v tabulce vtable nezahrnují základní členů rozhraní.  
  
## <a name="resolution"></a>Rozlišení  
 Nevystavujte rozhraní třídy. Definovat explicitní rozhraní a použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut ho.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Následující příklad zpráva pro je `QueryInterface` volání COM – viditelné třídy `Derived` , je odvozena od jiných COM – viditelné třídy `Base`.  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
