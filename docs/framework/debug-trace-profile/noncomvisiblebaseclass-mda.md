---
title: nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb0810a9e0ffce825abecc87eb2698920209d86f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753761"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
`nonComVisibleBaseClass` Pomocníka spravovaného ladění (MDA) se aktivuje při `QueryInterface` je provedeno volání pomocí nativní nebo nespravovaného kódu na obálka volatelná aplikacemi COM (CCW) COM – viditelné spravované třídy, která je odvozena ze základní třídy, které nejsou viditelné modelu COM.  `QueryInterface` Volání způsobí, že MDA aktivovat pouze v případech, kde požadavky na třídy rozhraní nebo výchozí volání `IDispatch` COM-viditelných spravované třídy.  MDA není aktivuje se, když `QueryInterface` je pro explicitní rozhraní, který má <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> použít atribut a je explicitně implementované COM – viditelné třídy.  
  
## <a name="symptoms"></a>Příznaky  
 A `QueryInterface` volání z nativního kódu, který je neúspěšné s chybou HRESULT COR_E_INVALIDOPERATION.  Hodnota HRESULT mohou být způsobeny runtime zákaz `QueryInterface` volání, které by mohly způsobit aktivace toto MDA.  
  
## <a name="cause"></a>Příčina  
 Modul runtime nemůže povolit `QueryInterface` volání pro rozhraní třídy nebo výchozí `IDispatch` rozhraní COM – viditelné třídy, která je odvozena z třídy, který není viditelný modulem COM z důvodu potenciální problémy se správou verzí.  Například, pokud žádné veřejné členy byly přidány na základní třídu, která není viditelný modulem COM, existující klienti modelu COM pomocí odvozené třídy může potenciálně narušit vzhledem k tomu tabulku vtable, který obsahuje členy základní třídy odvozené třídy by změněny, Změňte.  Explicitní rozhraní vystavit rozhraní COM nemají tento problém, protože v tabulce vtable neobsahují základních členů rozhraní.  
  
## <a name="resolution"></a>Řešení  
 Nezveřejňujte třídy rozhraní. Definujte explicitní rozhraní a použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut k němu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Tady je ukázková zpráva pro `QueryInterface` volání COM – viditelné třídy `Derived` , která je odvozena z třídy není viditelný pro COM `Base`.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
