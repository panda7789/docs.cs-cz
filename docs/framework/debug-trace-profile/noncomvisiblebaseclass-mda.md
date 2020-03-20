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
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181792"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass – pomocník spravovaného ladění (MDA)
Spravovaný `nonComVisibleBaseClass` pomocník pro ladění (MDA) `QueryInterface` je aktivován, když je volání provedeno nativním nebo nespravovaným kódem na telefonním obalu COM (CCW) spravované třídy viditelné pro COM, která je odvozena ze základní třídy, která není viditelná pro COM.  Volání `QueryInterface` způsobí, že MDA aktivovat pouze v případech, `IDispatch` kdy volání požaduje rozhraní třídy nebo výchozí com viditelné spravované třídy.  MDA není aktivován, `QueryInterface` pokud je pro explicitní <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> rozhraní, které má atribut použít a je explicitně implementována com viditelné třídy.  
  
## <a name="symptoms"></a>Příznaky  
 Volání `QueryInterface` z nativního kódu, který selhává s COR_E_INVALIDOPERATION HRESULT.  HRESULT může být způsobeno za běhu nepovolování `QueryInterface` volání, které by způsobilo aktivaci tohoto MDA.  
  
## <a name="cause"></a>Příčina  
 Modul runtime `QueryInterface` nemůže povolit volání `IDispatch` pro rozhraní třídy nebo výchozí rozhraní třídy viditelné pro COM, která je odvozena z třídy, která není viditelná pro COM z důvodu potenciálních problémů se správu verzí.  Například pokud všechny veřejné členy byly přidány do základní třídy, která není viditelné COM, existující com klienti pomocí odvozené třídy by potenciálně přerušit, protože vtable odvozené třídy, která obsahuje členy základní třídy, by být změněny takové Změnit.  Explicitní rozhraní vystavená com nemají tento problém, protože nezahrnují základní členy rozhraní v vtable.  
  
## <a name="resolution"></a>Řešení  
 Nezveřejňujte rozhraní třídy. Definujte explicitní rozhraní <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a aplikujte na něj atribut.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Následuje ukázková zpráva pro `QueryInterface` volání třídy `Derived` viditelné pro COM, která je odvozena z třídy, `Base`která není viditelná jako COM .  
  
```output
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
